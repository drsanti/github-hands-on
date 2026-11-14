# บท 02 · สร้าง Repository แรก

## เป้าหมาย

สร้าง Repository ของตนเอง เลือกการมองเห็น และเริ่ม README ที่อธิบายโปรเจกต์ได้

## สถานการณ์

ต้องการพื้นที่เก็บประวัติและส่งลิงก์ผลงานให้ผู้สอน โดยเลือกได้ว่าใครเปิดอ่านได้

## แนวคิดที่ต้องใช้

Public เปิดให้ผู้อื่นอ่านได้ แต่ไม่ได้ให้ทุกคน Push ได้ Private จำกัดผู้อ่านตามสิทธิ์ README เป็นจุดเริ่มอ่านโปรเจกต์ ส่วน License ระบุสิทธิ์การนำผลงานไปใช้ Public ไม่ได้แปลว่าใช้ซ้ำได้ทุกกรณี

## Demo โดยผู้สอน

สาธิตหน้า New repository การเลือก Visibility และ Add README อธิบายชื่อ `OWNER/my-first-project` โดยแทน OWNER ด้วยบัญชีจริง

## ลงมือทำ

1. เข้าสู่ GitHub เลือกเมนู `+` → New repository
2. เลือก Owner เป็นบัญชีของตนเอง ตั้งชื่อ `my-first-project` ถ้ามีชื่อนี้แล้วให้ใช้ `my-first-project-workshop` และใช้ชื่อนั้นตลอด
3. ใส่ Description: `My first hands-on GitHub learning project.`
4. เลือก Public หากต้องการให้เปิดตรวจผ่านลิงก์ หรือ Private แล้วให้สิทธิ์ผู้สอนตามที่ตกลงกัน
5. เปิด Add README ยังไม่ต้องเลือก `.gitignore` หรือ License ในกิจกรรมนี้ อย่าใส่ License โดยไม่รู้เงื่อนไข
6. เลือก Create repository แล้วตรวจว่ามี `README.md` และ default branch เป็น `main`
7. เปิด README → Edit ใส่ข้อความนี้ โดยเปลี่ยนชื่อเป็นชื่อเล่นของตนเอง:

```markdown
# My First Project

โปรเจกต์ฝึกใช้งาน GitHub ผ่านการลงมือทำ

## About Me

สวัสดี ฉันชื่อ Demo สนใจเรียนรู้การทำงานร่วมกันด้วย GitHub
```

8. เลือก Commit changes ใส่ข้อความ `docs: introduce project and author` เลือก Commit directly to `main` แล้วบันทึก
9. กลับหน้า Code ตรวจว่า README แสดงเนื้อหาใหม่และคัดลอก URL Repository

## Checkpoint

- [ ] Repository อยู่ภายใต้บัญชีตนเองและมี README
- [ ] รู้ว่าเลือก Public หรือ Private เพราะอะไร
- [ ] README แสดงชื่อโปรเจกต์และคำแนะนำตัว ไม่มีข้อมูลลับ

## Mini Challenge

เพิ่มหัวข้อ `Learning Goals` พร้อมเป้าหมาย 2 ข้อ แล้วสร้าง Commit แยกที่บอกว่าเพิ่มอะไร

## คำถามทบทวน

1. Public repository หมายความว่าใครก็แก้ `main` ได้หรือไม่?
2. ถ้าใช้ Private จะส่งลิงก์อย่างเดียวให้เพื่อนอ่านได้หรือไม่?
3. ทำไม README ควรอธิบายวัตถุประสงค์มากกว่ามีเพียงชื่อ?

[ก่อนหน้า](../01-git-and-github/README.md) · [ใบงาน 02](../../worksheets/02-first-repository.md) · [ถัดไป: บท 03](../03-files-and-commits/README.md)
