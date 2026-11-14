# บท 04 · ทำงานบนเครื่องด้วย GitHub Desktop

## เป้าหมาย

Clone โปรเจกต์ แก้ไฟล์ ตรวจ Diff, Commit, Push และรับงานด้วย Fetch/Pull ได้

## สถานการณ์

ต้องการแก้หลายไฟล์บนเครื่องแล้วส่งขึ้น GitHub รวมถึงรับการเปลี่ยนแปลงที่ทำจากเว็บกลับมา

## แนวคิดที่ต้องใช้

| การกระทำ | ผล |
|---|---|
| Clone | สร้างสำเนา Repository พร้อมประวัติลงเครื่อง ต่างจาก Download ZIP ที่ไม่ได้เตรียม Git history/remote ให้ทำงานต่อแบบ Clone |
| Save | บันทึกไฟล์ที่กำลังแก้ |
| Commit | บันทึกการเปลี่ยนแปลงที่เลือกใน Git บนเครื่อง |
| Push | ส่ง Commits ของ Branch ไป Remote |
| Fetch | รับข้อมูล/ประวัติล่าสุดจาก Remote โดยยังไม่รวมเข้า Branch ที่ทำงาน |
| Pull | รับแล้วรวมการเปลี่ยนแปลงของ Remote branch เข้าสู่ Local branch |

ตรวจ Current Repository และ Current Branch ทุกครั้ง เริ่มบทนี้บน `main` ที่ไม่มีงานค้าง

## Demo โดยผู้สอน

แก้ไฟล์และ Save ให้ดูว่า Desktop แสดง Changes จากนั้น Commit แล้วตรวจเว็บก่อน Push เพื่อแสดงว่างานยังไม่ขึ้น GitHub

## ลงมือทำ

1. เปิด Desktop → File → Clone repository เลือก `OWNER/my-first-project` หรือวาง URL Repository ของตนในแท็บ URL
2. เลือก Local path เช่น `Documents/GitHub/my-first-project` แล้ว Clone อย่าเลือกโฟลเดอร์โปรเจกต์อื่นที่มีงานอยู่แล้ว
3. เลือก Repository → Open in Visual Studio Code หรือเปิดโฟลเดอร์นั้นในโปรแกรมแก้ไข
4. เพิ่มบรรทัด `- ฝึกแก้ไฟล์จากคอมพิวเตอร์ด้วย GitHub Desktop` ใน `notes/learning-log.md` แล้ว Save
5. นำ [ภาพตัวอย่าง](../../assets/images/project-icon.svg) ไปบันทึกเป็นไฟล์ `assets/project-icon.svg` ภายในโปรเจกต์ฝึก และเพิ่ม `![Project icon](assets/project-icon.svg)` ใน README ถ้าเปิดภาพในเว็บให้ใช้การดาวน์โหลดไฟล์ SVG จริง ไม่ใช่บันทึกหน้า HTML
6. กลับ Desktop → Changes ตรวจรายการไฟล์และ Diff เลือกเฉพาะไฟล์กิจกรรมนี้ กรอก Summary `docs: add desktop learning note and project icon` แล้ว Commit to main
7. เปิดเว็บสังเกตว่ายังเป็นเนื้อหาเดิม จากนั้นกลับ Desktop → Push origin รีเฟรชเว็บ ตรวจข้อความและภาพ
8. บนเว็บแก้ Learning log เพิ่ม `- รับการเปลี่ยนแปลงจากเว็บไซต์กลับเครื่อง` แล้ว Commit to main
9. กลับเครื่องยังไม่แก้อะไรเพิ่ม เลือก Fetch origin แล้ว Pull origin เมื่อมี Commits ใหม่
10. เปิดไฟล์บนเครื่อง ตรวจว่าบรรทัดจากเว็บเข้ามาแล้ว และ Changes ว่าง

ถ้า Push ถูกปฏิเสธเพราะ Remote มีงานใหม่ ให้ Commit งานบนเครื่องก่อน จากนั้น Fetch/Pull อ่านและแก้ Conflict ถ้ามี แล้ว Push อีกครั้ง ไม่ใช้ Force push เพื่อข้ามปัญหา

## Checkpoint

- [ ] บอก Local path ของ Repository ที่ Clone ได้
- [ ] เว็บมี Commit และภาพที่ส่งจากเครื่อง
- [ ] เครื่องมีข้อความที่เพิ่มจากเว็บ และไม่มี Changes ค้าง

## Mini Challenge

เพิ่มหัวข้อเล็ก ๆ บนเครื่อง ส่งขึ้นเว็บ แล้วเพิ่มข้อความอีกหนึ่งบรรทัดบนเว็บและรับกลับเครื่องโดยไม่ดูขั้นตอน

## คำถามทบทวน

1. Save แล้วทำไมไม่มี Commit ใหม่?
2. Commit แล้วเพื่อนยังไม่เห็น ต้องตรวจอะไรต่อ?
3. Fetch สำเร็จแต่เนื้อหาไฟล์ยังไม่เปลี่ยน เป็นไปได้เพราะอะไร?

[ก่อนหน้า](../03-files-and-commits/README.md) · [ใบงาน 04](../../worksheets/04-github-desktop.md) · [ถัดไป: บท 05](../05-branches/README.md)
