# ปัญหาที่พบบ่อย

เริ่มตรวจจาก Current Repository, Current Branch, Changes และบัญชีที่เข้าสู่ระบบ ก่อนลองคำสั่งแก้ปัญหา

| อาการ | สิ่งที่ตรวจและวิธีดำเนินการ |
|---|---|
| Save แล้วเว็บไม่เปลี่ยน | กลับ Desktop ตรวจ Diff → Commit → Push แล้วรีเฟรชเว็บให้ตรง Branch |
| Desktop ไม่เห็นไฟล์ที่แก้ | ตรวจ Local path ไฟล์ต้องอยู่ในโฟลเดอร์ที่ Clone และไม่ถูก ignore |
| Commit ไม่ได้เพราะไม่มี Changes | ตรวจว่าบันทึกไฟล์แล้วหรือเนื้อหายังเหมือนเดิม ถ้า Commit ไปแล้วให้ดู History |
| Push ไม่ได้/Permission denied | ตรวจบัญชี Remote และสิทธิ์ Collaborator รับคำเชิญให้ครบ หรือใช้ Fork ตามข้อตกลง |
| Push ถูกปฏิเสธเพราะ Remote มีงานใหม่ | เก็บงานด้วย Commit ก่อน Fetch/Pull แก้ Conflict แล้ว Push ไม่ใช้ Force push ข้าม |
| Fetch แล้วไฟล์ไม่เปลี่ยน | Fetch ไม่รวมงาน ให้ตรวจว่ามี Pull origin และเลือก Branch ที่ถูก |
| Clone ไม่ได้ | ตรวจ URL, สิทธิ์ Private repo, เครือข่าย และโฟลเดอร์ปลายทางที่ว่าง |
| มีงานค้างตอนสลับ Branch | อยู่ Branch เดิม ตรวจและ Commit งานที่ต้องเก็บก่อน อย่ากด Discard โดยไม่อ่าน |
| ไม่เห็น Branch บนเว็บ | Branch อาจยัง Local ให้ Publish branch/Push และตรวจ Repository ปลายทาง |
| PR ไม่มีอะไรให้เปรียบเทียบ | ตรวจ Base/Compare ว่าต่างกัน Branch ถูก Push แล้วหรือ Merge ไปแล้วหรือยัง |
| เพื่อน Approve ไม่ได้ | ตรวจว่าไม่ได้เป็นผู้เขียน PR เอง และตรวจบัญชี/สิทธิ์/ข้อจำกัดของ Repository |
| Merge แล้วเครื่องยังเป็นรุ่นเก่า | เลือก main → Fetch/Pull โดยไม่มีงานค้าง |
| ลิงก์/ภาพเสีย | ตรวจตำแหน่งสัมพันธ์กับไฟล์ Markdown, ตัวพิมพ์เล็กใหญ่ และไฟล์ที่ Push จริง |
| Conflict ไม่เกิดในบท 07 | ตรวจว่าสร้าง title-a และ title-b จากฐานเดิมก่อน Merge และแก้บรรทัดเดียวให้ต่างกัน |
| แก้ Conflict แล้วปุ่มยังไม่พร้อม | Save ทุกไฟล์ ตรวจ markers ที่เหลือ และกลับ Desktop เพื่อทำ Continue merge/Commit merge |
| Closes ไม่ปิด Issue | ตรวจ keyword ใน PR description, เลข Issue จริง และ Merge เข้า default branch แล้วหรือยัง |
| เผลอ Commit Secret | ยกเลิก/เปลี่ยน Secret ทันที แจ้งผู้ดูแล Revert ไม่ลบประวัติ ดูเอกสารอ้างอิงด้านล่าง |

ถ้าเจอข้อความไม่ตรงกับคู่มือ ให้จดข้อความผิดพลาดที่ไม่เปิดเผยข้อมูลลับ พร้อม Repository/Branch และขั้นตอนก่อนเกิดปัญหาแล้วขอผู้สอนช่วย ไม่ทดลองลบ Repository เพื่อเริ่มใหม่โดยไม่เก็บงาน

[เอกสารต้นฉบับ](../docs/references.md) · [ภาคผนวก](README.md)
