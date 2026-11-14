# CLI-05 · Fetch, Pull, Push และ Remote

## เป้าหมายและสถานการณ์

ส่งงานจากเครื่อง รับงานจากอีกเครื่อง และอธิบายได้ว่าทำไม Push บางครั้งถูกปฏิเสธ ใช้สำเนา Clone ที่สองจำลองผู้ร่วมงานได้โดยไม่ต้องเปลี่ยนเครื่อง

## คำสั่งที่ต้องใช้

| คำสั่ง | ผล |
|---|---|
| `git remote -v` | ที่อยู่ Remote ตรวจให้ถูกก่อนส่งงาน |
| `git branch -vv` | Branch และ Upstream พร้อมสถานะตามข้อมูลที่ Fetch ไว้ |
| `git fetch origin` | รับ Git objects และอัปเดต Remote-tracking refs เช่น origin/main โดยยังไม่รวมเข้า Local main |
| `git pull --ff-only` | รับงานและอัปเดต Branch เมื่อ Fast-forward ได้ หากประวัติแยกกันจะหยุด |
| `git push` | ส่ง Commits ของ Branch ตาม Upstream/การตั้งค่า |

origin/main เป็นข้อมูล Remote ครั้งล่าสุดที่ Fetch มา ไม่ใช่การเชื่อมแบบเรียลไทม์

## ลงมือทำ A · รับงานจากสำเนาที่สอง

ในสำเนาหลัก:

```bash
git switch main
git pull --ff-only
git status --short
```

ใน Terminal อีกหน้าต่าง เปิดสำเนา `my-first-project-cli-copy` จาก CLI-02 หรือ Clone ใหม่ไว้นอก Repository หลัก ตั้ง Identity แบบ local ถ้าเครื่องนี้ยังไม่ได้ตั้ง จากนั้น:

```bash
git switch main
git pull --ff-only
printf '\n- Updated from the second clone.\n' >> notes/learning-log.md
git add notes/learning-log.md
git commit -m "docs: record second clone update"
git push
```

กลับสำเนาหลัก:

```bash
git fetch origin
git status --short --branch
git log --oneline main..origin/main
git diff main..origin/main -- notes/learning-log.md
```

เปิดไฟล์ใน editor ตอนนี้ Local main ยังไม่มีบรรทัดใหม่ จึงสั่ง:

```bash
git pull --ff-only
git status --short --branch
```

ไฟล์ควรอัปเดตแล้ว การ Push ตรง main ในส่วนนี้เป็นข้อยกเว้นเพื่อจำลองการ Sync ของ Repository ฝึกที่ไม่ตั้ง Protection งานทีมปกติใช้ Branch/PR

## ลงมือทำ B · Push rejection และประวัติที่แยกกัน

เมื่อทั้งสองสำเนาตรงกัน สร้าง Local commit บน main ของสำเนาหลักโดยเปลี่ยนเฉพาะหัวข้อบรรทัดแรกใน README เป็น `# My First CLI Project` แล้ว Add/Commit แต่ยังไม่ Push จากสำเนาที่สองเพิ่มบรรทัดใน Learning log แล้ว Commit/Push main จากนั้นกลับสำเนาหลักลอง `git push` ควรถูกปฏิเสธเพราะ Remote มี Commit ที่ Local ยังไม่มี การแก้คนละไฟล์นี้ช่วยแยกการฝึก Divergence ออกจาก Conflict ในบท 07

```bash
git fetch origin
git log --oneline --graph --decorate --all -12
git pull --ff-only
```

`--ff-only` ต้องหยุดเมื่อประวัติ Diverged ไม่ใช่ข้อผิดพลาดที่ควร Force push ข้าม ตรวจ Diff และยืนยันว่าเป็นงานทดลองที่ต้องเก็บทั้งสองฝั่ง แล้วรวมโดยเลือกวิธี Merge อย่างชัดเจน:

```bash
git merge --no-edit origin/main
git log --oneline --graph --decorate -8
git push
```

การ Merge นี้เริ่มจากงานค้างว่าง หากเกิด Conflict ให้ใช้ [CLI-07](../07-conflicts-and-recovery/README.md) หรือยกเลิก Merge ที่กำลังค้างด้วย `git merge --abort` แล้วขอผู้สอนช่วย การ Abort ใช้เมื่อ Merge ยังไม่เสร็จ ไม่ใช่ย้อน Merge ที่ Commit แล้ว

## Demo และ Checkpoint

ผู้สอนหยุดก่อน Pull ให้ผู้เรียนเทียบ Local main กับ origin/main

- [ ] พิสูจน์ว่า Fetch ยังไม่แก้ไฟล์ใน Working tree ได้
- [ ] อ่านสถานะ Behind/Ahead และ Graph หลัง Fetch ได้
- [ ] Push ถูกปฏิเสธในกรณี Diverged แล้วรวมโดยเก็บงานสองฝั่ง ไม่ Force push

## Mini Challenge และทบทวน

อธิบายว่ากรณี Authentication failed กับ Non-fast-forward rejection ควรตรวจอะไรต่างกัน แล้วให้คู่ฝึกแสดง Merge ล่าสุดที่มี Parent สองชุดด้วย `git show --no-patch --pretty=raw HEAD`

[ก่อนหน้า](../04-branches-and-merges/README.md) · [ใบงาน](../../../worksheets/command-line/05-sync-and-remotes.md) · [ถัดไป](../06-pull-requests/README.md)
