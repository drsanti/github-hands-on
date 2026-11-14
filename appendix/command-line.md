# Command Line ทางเลือก

ส่วนนี้สำหรับผู้ที่ต้องการเชื่อมแนวคิดกับคำสั่ง Git **ไม่จำเป็นต้องใช้เพื่อผ่านกิจกรรมหลัก** ต้องติดตั้ง Git และตั้งค่าการเข้าสู่ระบบสำหรับ Terminal แยกตามเครื่อง การใช้ Desktop ได้ไม่ได้รับประกันว่า Terminal พร้อมใช้ทันที

แทน OWNER และชื่อ Repository ด้วยค่าจริง ทำในโฟลเดอร์ฝึก อย่า Clone ซ้อนใน Repository อื่น

## Clone และตรวจสถานะ

```bash
git clone https://github.com/OWNER/my-first-project.git
cd my-first-project
git status
git branch --show-current
```

## รับงาน สร้าง Branch และส่งการเปลี่ยนแปลง

เริ่มเมื่อไม่มีงานค้าง แก้และ Save ไฟล์ `notes/learning-log.md` หลังสร้าง Branch แล้วจึงทำส่วน Commit

```bash
git switch main
git pull --ff-only
git switch -c improve-learning-log
```

หลังแก้ไฟล์:

```bash
git diff
git add notes/learning-log.md
git diff --staged
git commit -m "docs: improve learning log"
git push -u origin improve-learning-log
```

จากนั้นเปิด PR และ Review บนเว็บไซต์ตามบท 06 `git pull --ff-only` จะหยุดเมื่อรวมแบบ Fast-forward ไม่ได้ ให้ตรวจสาเหตุแทนการสั่ง Force push

## เทียบกับ Desktop

| Desktop | Git |
|---|---|
| Changes | `git status` และ `git diff` |
| เลือกไฟล์ที่จะ Commit | `git add PATH` |
| Commit | `git commit` |
| Fetch origin | `git fetch origin` |
| Pull origin | `git pull` (พฤติกรรมรวมงานขึ้นกับการตั้งค่า) |
| Push origin | `git push` |
| History | `git log --oneline` |

ใช้ชื่อไฟล์เฉพาะแทน `git add .` ในการฝึกแรก เพื่อเห็นชัดว่ากำลังจะบันทึกอะไร ไม่สอน Reset/Force push เป็นวิธีแก้ปัญหาทั่วไปในหลักสูตรผู้เริ่มต้น

[ภาคผนวก](README.md)
