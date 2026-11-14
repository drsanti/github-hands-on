# CLI-03 · Working Tree, Staging และ Commit

## เป้าหมายและสถานการณ์

เลือกบันทึกเฉพาะงานที่ตั้งใจ และอ่านความต่างของไฟล์ที่ Save, Stage และ Commit ได้ เริ่มในโฟลเดอร์โปรเจกต์หลักจาก CLI-02 บน main ที่ไม่มีงานค้าง

## คำสั่งและเหตุผล

| คำสั่ง | ใช้ดู/ทำอะไร |
|---|---|
| `git status --short` | สถานะไฟล์ คอลัมน์แรกคือ Index/Stage คอลัมน์สองคือ Working tree |
| `git diff` | งานที่ยังไม่ Stage ของไฟล์ที่ Git ติดตามแล้ว |
| `git add PATH` | นำเนื้อหาไฟล์ ณ ตอนสั่งไปไว้ใน Staging |
| `git diff --staged` | งานที่เตรียมไว้สำหรับ Commit ถัดไป |
| `git log --oneline` | ประวัติ Commits แบบย่อ |
| `git show COMMIT_SHA` | เนื้อหาการเปลี่ยนแปลงใน Commit ที่เลือก |

ไฟล์ Untracked ยังไม่ปรากฏเนื้อหาใน `git diff` ต้องอ่านไฟล์และ Stage ก่อนจึงดูผ่าน `git diff --staged` ได้

## ลงมือทำ A · เห็นสถานะทั้งสามจุด

```bash
mkdir -p notes
printf '# Learning Log\n\n- Save changes a file.\n' > notes/learning-log.md
git status --short
git diff
git add notes/learning-log.md
git diff --staged
```

หยุดอ่านผล `??` คือไฟล์ยังไม่ Track หลัง Add จะเห็น `A ` ต่อท้ายเพิ่มอีกหนึ่งบรรทัดโดย **ยังไม่ Add รอบใหม่**:

```bash
printf '\n- Commit records selected changes.\n' >> notes/learning-log.md
git status --short
git diff
git diff --staged
```

ควรเห็น `AM`: Stage มีเนื้อหาก่อนเพิ่มบรรทัด แต่ Working tree มีเนื้อหาใหม่กว่า นี่คือเหตุผลที่ Save หลัง Add แล้วต้อง Add อีกครั้งถ้าต้องการนำงานใหม่เข้า Commit

```bash
git add notes/learning-log.md
git diff --staged
git commit -m "docs: add learning log"
```

## ลงมือทำ B · Unstage โดยไม่ทิ้งเนื้อหา

เพิ่ม Skills ใน README ด้วย editor และ Save จากนั้น:

```bash
git add README.md
git restore --staged README.md
git status --short
git diff
```

README ยังมีข้อความที่แก้ แต่ไม่อยู่ใน Staging ให้ตรวจแล้ว Stage/Commit อีกครั้งด้วย Message `docs: add skills section` การ Unstage ไม่ใช่การลบงาน

## ลงมือทำ C · Ignore และประวัติ

สร้าง `.gitignore` ใหม่ด้วย editor ใส่ `scratch/` และ `*.log` คนละบรรทัด ถ้ามีไฟล์เดิมให้เพิ่มต่อโดยไม่ทับเนื้อหาเดิม จากนั้น:

```bash
mkdir -p scratch
printf 'Disposable local note\n' > scratch/local-note.txt
git status --short
git check-ignore -v scratch/local-note.txt
git add .gitignore
git commit -m "chore: ignore local scratch files"
git log --oneline -5
git show --stat HEAD
git log --oneline -- notes/learning-log.md
git push
```

Ignore มีผลกับไฟล์ที่ยังไม่ถูก Track การเพิ่มชื่อไฟล์ใน .gitignore ไม่ลบประวัติของไฟล์ที่ Commit แล้ว หลีกเลี่ยง `git add .` จนกว่าจะอ่านรายการไฟล์ได้ครบ

## เพิ่มภาพประกอบเพื่อชิ้นงานปลายทาง

นำ [ภาพตัวอย่าง](../../../assets/images/project-icon.svg) ไปบันทึกเป็น `assets/project-icon.svg` ในโปรเจกต์ฝึก สร้างโฟลเดอร์ assets ก่อนด้วย `mkdir -p assets` เพิ่ม `![Project icon](assets/project-icon.svg)` ใน README แล้วตรวจ Preview จากนั้น `git add README.md assets/project-icon.svg`, ตรวจ staged diff, Commit และ Push เหมือนขั้นตอนก่อนหน้า ตรวจว่าดาวน์โหลดไฟล์ SVG จริง ไม่ใช่หน้า HTML

## Demo และ Checkpoint

ผู้สอนหยุดหลัง Add แล้ว Save อีกครั้ง ให้ผู้เรียนทายว่า Commit จะได้ข้อความชุดใด

- [ ] อธิบาย `??`, `A `, ` M` และ `AM` ได้จากงานจริง
- [ ] มี Commits ของ Learning log, Skills และ Ignore แยกกัน
- [ ] Scratch file ไม่ถูก Track และ History บน GitHub ตรงกับที่ Push

## Mini Challenge และทบทวน

แก้สองไฟล์แล้ว Commit เฉพาะไฟล์หนึ่งก่อน จากนั้น Commit อีกไฟล์แยก อธิบายจาก `git diff` และ `git diff --staged` ว่าสิ่งใดกำลังจะถูกบันทึก

[ก่อนหน้า](../02-repositories/README.md) · [ใบงาน](../../../worksheets/command-line/03-staging-and-commits.md) · [ถัดไป](../04-branches-and-merges/README.md)
