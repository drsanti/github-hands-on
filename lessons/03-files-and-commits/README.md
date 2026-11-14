# บท 03 · ไฟล์ Markdown และ Commit history

## เป้าหมาย

จัดไฟล์และโฟลเดอร์ เขียน Markdown และตรวจสอบการเปลี่ยนแปลงจาก Commit history ได้

## สถานการณ์

หน้าแนะนำตัวเริ่มยาว ต้องแยกบันทึกการเรียนออกเป็นอีกไฟล์ และบันทึกงานเป็นส่วนที่อธิบายได้

## แนวคิดที่ต้องใช้

| Markdown | ใช้แสดง |
|---|---|
| `# Title` / `## Section` | ชื่อเรื่อง/หัวข้อ |
| `- Item` | รายการ |
| `**Important**` | ตัวหนา |
| `[Learning log](notes/learning-log.md)` | ลิงก์ไฟล์ภายใน |
| `![คำอธิบาย](assets/project-icon.svg)` | รูปภาพ เมื่อมีไฟล์จริงตามตำแหน่ง |

Commit หนึ่งรายการควรอธิบายงานหนึ่งเรื่อง เช่น `docs: add skills section` ดีกว่า `update` หรือ `final` คำนำ `docs:` เป็นข้อตกลงที่ช่วยอ่าน ไม่ใช่ข้อบังคับของ Git

## Demo โดยผู้สอน

แก้ข้อความหนึ่งบรรทัด เปิด Preview ก่อน Commit และเปิด History หลัง Commit เพื่อเปรียบเทียบผล

## ลงมือทำ

1. เปิด README บนเว็บ เพิ่ม `## Skills` และรายการทักษะ 2–3 ข้อ Preview แล้ว Commit ด้วย `docs: add skills section`
2. เลือก Add file → Create new file ตั้งชื่อ `notes/learning-log.md` เครื่องหมาย `/` ใช้สร้างเส้นทางโฟลเดอร์
3. ใส่หัวข้อ `# Learning Log` และเขียนว่า Save กับ Commit ต่างกันอย่างไร Commit ด้วย `docs: add learning log`
4. กลับ README เพิ่มลิงก์ `[Learning log](notes/learning-log.md)` และหัวข้อ `## Project Ideas` พร้อมแนวคิดหนึ่งเรื่อง Commit ด้วย `docs: link learning log and add project idea`
5. คลิกลิงก์ Learning log จาก README ตรวจว่าเปิดไฟล์จริงได้
6. เปิด Commits เลือกแต่ละรายการ ดูไฟล์ที่เปลี่ยนและเปรียบเทียบกับ Commit message
7. ฝึกเพิ่มไฟล์ `notes/scratch.md` ใส่ `Temporary practice file` และ Commit จากนั้นใช้เมนู Delete file ของไฟล์นั้นและ Commit การลบเป็นอีกรายการ
8. เปิด Commit ของการลบ สังเกตว่าไฟล์หายจากเวอร์ชันปัจจุบันแต่ยังอยู่ในประวัติ

อย่าลบไฟล์จริงเพื่อทดลอง คำว่า Delete ในที่นี้ใช้กับไฟล์ฝึก `scratch.md` เท่านั้น

## Checkpoint

- [ ] มี `README.md` และ `notes/learning-log.md` พร้อมลิงก์ที่เปิดได้
- [ ] มีอย่างน้อย 3 Commits ที่ทำงานต่างกันและอธิบาย Diff ได้
- [ ] ลบไฟล์ฝึกแล้ว แต่ยังเปิดเนื้อหาก่อนลบจาก History ได้

## Mini Challenge

แก้คำผิดหนึ่งตำแหน่งใน Learning log แล้วตั้ง Commit message ให้เพื่อนรู้ได้ว่าแก้อะไร ทดลองเปิดหน้าไฟล์จาก Commit เก่าเพื่ออ่านอย่างเดียว

## คำถามทบทวน

1. ทำไมต้องเปิด Preview และ Diff ก่อนบันทึก?
2. ลบไฟล์ปัจจุบันแล้วทำไมยังอ่านเวอร์ชันเก่าได้?
3. Commit หลายเรื่องที่ไม่เกี่ยวกันในครั้งเดียวทำให้ Review ยากอย่างไร?

[ก่อนหน้า](../02-first-repository/README.md) · [ใบงาน 03](../../worksheets/03-files-and-commits.md) · [ถัดไป: บท 04](../04-github-desktop/README.md)
