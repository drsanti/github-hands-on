# CLI-07 · Conflict, Restore และ Revert

## เป้าหมายและสถานการณ์

แก้บรรทัดที่สอง Branch เห็นต่างกัน และเลือกวิธีย้อนงานตามสถานะได้ ทำใน Repository ฝึกหลักที่ไม่มีงานค้างเท่านั้น กิจกรรมนี้ใช้ Local branches ที่ไม่ Publish เพื่อทดลอง Merge โดยไม่กระทบ main

## ลงมือทำ A · เตรียมฐานร่วม

```bash
git switch main
git pull --ff-only
git status --short
git switch -c conflict-base
printf '# Workshop Plan\n\nWorkshop title: GitHub Basics\n' > notes/workshop-title.md
git add notes/workshop-title.md
git commit -m "docs: add base workshop title"
git switch -c title-a
```

แก้บรรทัดสุดท้ายใน `notes/workshop-title.md` เป็น `Workshop title: GitHub for Beginners` แล้ว Save:

```bash
git add notes/workshop-title.md
git commit -m "docs: use beginner workshop title"
git switch -c title-b conflict-base
```

title-b ต้องเริ่มจาก conflict-base เดิม **ไม่ใช่ title-a** แก้บรรทัดเดียวกันเป็น `Workshop title: GitHub Hands-On` แล้ว Save:

```bash
git add notes/workshop-title.md
git commit -m "docs: use hands-on workshop title"
git switch -c conflict-integration conflict-base
git merge --ff-only title-a
git merge --no-edit title-b
```

Merge ครั้งสุดท้ายควรหยุดด้วย CONFLICT นี่คือผลที่ต้องการ ไม่ต้องรันบล็อกถัดไปเพื่อข้ามโดยไม่อ่าน

## ลงมือทำ B · ตรวจและแก้ Conflict

```bash
git status
git diff --name-only --diff-filter=U
git diff
```

เปิดไฟล์ที่ขัดกัน จะมีส่วน `<<<<<<<`, `=======`, `>>>>>>>` อ่านข้อความสองฝั่งแล้วเปลี่ยนทั้งช่วงเป็น:

```markdown
# Workshop Plan

Workshop title: GitHub Hands-On for Beginners
```

ลบ markers ให้ครบ Save แล้ว:

```bash
git add notes/workshop-title.md
git diff --cached --check
git diff --staged
git diff --name-only --diff-filter=U
git commit -m "docs: resolve workshop title conflict"
git log --oneline --graph --decorate -10
```

รายการไฟล์ Unmerged ต้องว่าง ถ้าต้องการยกเลิก **ก่อนสร้าง Merge commit** ให้ใช้ `git merge --abort` แล้วลอง Merge title-b อีกครั้ง ไม่ใช่ Add/Commit การแก้และ Abort ทั้งสองอย่างต่อกัน

## ลงมือทำ C · แยกการย้อนงานสามแบบ

| สถานะ | วิธี | ผลต่อประวัติ |
|---|---|---|
| Stage ผิดไฟล์ | `git restore --staged PATH` | เอาออกจาก Stage แต่เก็บงานที่แก้ |
| แก้ไฟล์ที่ Track แต่ยังไม่ Stage และต้องการทิ้งข้อความทดลอง | `git restore PATH` | เขียนทับ Working tree ด้วยเนื้อหาใน Index ไม่มี Commit ใหม่ |
| Commit งานไปแล้ว | `git revert COMMIT_SHA` | เพิ่ม Commit ใหม่ย้อนผล Commit ที่เลือก |

ฝึก Restore บน `conflict-integration` ซึ่งตอนนี้ไม่มีงานค้าง เปิด Learning log เติมบรรทัดทดลองที่ยอมทิ้งได้ Save **อย่า Stage** ตรวจ Diff แล้ว:

```bash
git diff -- notes/learning-log.md
git restore notes/learning-log.md
git status --short
```

`restore` บล็อกนี้ทิ้งการแก้ที่ยังไม่ Stage ของไฟล์นั้น ใช้เฉพาะข้อความทดลองนี้ ถ้าต้องเก็บงานให้ Commit แทน อย่าใช้ `git restore .` เพื่อทำให้ status ว่างโดยไม่ตรวจ

## ลงมือทำ D · Revert งานที่ Push แล้ว

```bash
git switch main
git pull --ff-only
git switch -c practice-revert
printf '\nTemporary note: remove this after practice\n' >> notes/learning-log.md
git add notes/learning-log.md
git commit -m "docs: add temporary practice note"
git push -u origin practice-revert
git show --stat HEAD
```

ตรวจว่า HEAD คือ Commit ข้อความทดลองที่เพิ่งสร้างและไม่มีงานค้างก่อนรัน:

```bash
git revert --no-edit HEAD
git push
git log --oneline -4
git diff main...practice-revert
git switch main
```

ประวัติมีทั้ง Commit ทดลองและ Revert แต่ Diff สุทธิจาก main ต้องว่าง ไม่ต้องเปิด PR ที่ไม่มีการเปลี่ยนแปลง หาก Revert มี Conflict ให้แก้ไฟล์, `git add PATH`, `git revert --continue` หรือเลือก `git revert --abort` เพื่อยกเลิก Revert ที่ยังค้าง

เก็บ Branch ฝึกไว้จนตรวจเสร็จ การ Revert ไม่ลบรหัสผ่านออกจากประวัติ ถ้าเคย Commit Secret จริงให้ยกเลิก/เปลี่ยน Secret และปรึกษาผู้ดูแลเรื่องการลบข้อมูลจากประวัติ

## Demo และ Checkpoint

ผู้สอนหยุดให้เห็น Conflict จริง อธิบายแต่ละ Parent ของ Merge commit และเทียบสถานะกับ Revert commit

- [ ] Conflict เกิดจากสอง Branch ที่แก้บรรทัดเดียวจากฐานเดิม
- [ ] conflict-integration มีข้อความสุดท้ายโดยไม่มี markers และ main ไม่ได้รับการทดลองนี้
- [ ] Restore ทำให้บรรทัดทดลองที่ยังไม่ Commit หาย
- [ ] practice-revert บน GitHub มี Commit เดิมและ Revert และไม่มี Diff สุทธิจาก main

## Mini Challenge และทบทวน

อธิบายว่ากรณีใดเลือก Unstage, Restore, Merge abort และ Revert พร้อมชี้หลักฐานของแต่ละกรณีจากการฝึก ไม่ทดลอง Reset/Rebase/Force push กับงานร่วมในบทนี้

[ก่อนหน้า](../06-pull-requests/README.md) · [ใบงาน](../../../worksheets/command-line/07-conflicts-and-recovery.md) · [ถัดไป](../08-issues-and-teamwork/README.md)
