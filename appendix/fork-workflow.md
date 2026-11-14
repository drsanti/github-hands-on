# ทางเลือก · ทำงานผ่าน Fork

ใช้เมื่อผู้เรียนไม่มีสิทธิ์ Push เข้า Repository ต้นทาง และต้นทางอนุญาตให้ Fork ได้ เริ่มกับโปรเจกต์ฝึก Public ก่อน ไม่จำเป็นสำหรับคู่ที่ใช้ Collaborator ในบท 06

## ขั้นตอน

1. B เปิด Repository ฝึกของ A → Fork สร้างสำเนาภายใต้บัญชี B
2. B Clone **Fork ของ B** ด้วย Desktop ไม่ใช่ Clone ต้นทางของ A แล้วพยายาม Push
3. สร้าง Branch เช่น `improve-learning-log` แก้ไฟล์ Commit และ Publish branch ไป Fork ของ B
4. เปิด PR บนเว็บ เลือก Base repository เป็น `A/my-first-project` และ Base branch เป็น main ส่วน Head/Compare repository เป็น Fork ของ B และ Branch งานของ B
5. A Review ให้ข้อเสนอแนะ B ปรับบน Branch เดิมแล้ว Push ไป Fork PR จะอัปเดต
6. A Merge เข้า Repository ต้นทาง หลังจากนั้นตรวจ main ของ A
7. ถ้าจะเริ่มงานใหม่ B เปิด Fork บนเว็บเลือก Sync fork → Update branch เมื่ออัปเดตได้โดยไม่มีข้อขัดแย้ง แล้วกลับ Desktop เลือก main → Fetch/Pull ก่อนสร้าง Branch ใหม่ หากแจ้งว่ามีงานต่างกัน/Conflict ให้หยุดอ่านรายละเอียดและขอผู้สอนช่วย ไม่ทิ้ง Commits ของตนเองเพื่อ Sync

Fork คือสำเนาบน GitHub ส่วน Clone คือสำเนาบนเครื่อง การ Merge PR ในต้นทางไม่ได้ทำให้ทุก Branch ใน Fork และเครื่องของ B อัปเดตเอง

[ต้นฉบับ GitHub](https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork) · [บท 06](../lessons/06-pull-requests/README.md)
