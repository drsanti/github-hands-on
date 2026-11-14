# บท 08 · Issues และ Workflow ของทีม

## เป้าหมาย

ระบุงานที่ตรวจรับได้ เชื่อม PR กับ Issue และทำงานครบวงจรด้วยตนเอง

## สถานการณ์

ผู้อ่านเปิดหน้าโปรเจกต์แล้วไม่รู้จะกลับหน้าแรกอย่างไร ทีมต้องเพิ่มลิงก์กลับ README โดยมีหลักฐานว่างานเสร็จแล้ว

## แนวคิดที่ต้องใช้

Issue ใช้บันทึกปัญหา/งาน PR แสดงการเปลี่ยนแปลงที่เสนอ Acceptance criteria ระบุสิ่งที่ต้องตรวจว่าผ่าน เช่น “กด Back to home แล้วเปิด README ได้” ชัดกว่า “ทำหน้าให้ดีขึ้น”

ข้อความ `Closes #N` ใน **PR description** เชื่อมและปิด Issue หมายเลข N เมื่อ Merge เข้า **default branch** ในกิจกรรมนี้คือ main หาก PR ชี้ไป Branch อื่นจะไม่ทำงานแบบเดียวกัน ต้องใช้เลข Issue จริงใน Repository นั้น ไม่เดาว่าเป็น #1 เพราะ Issue และ PR ใช้ลำดับเลขร่วมกัน

## Demo โดยผู้สอน

แปลงคำขอ “ทำเอกสารให้อ่านง่าย” เป็นงานเล็กพร้อมเกณฑ์ตรวจรับ แสดงความเชื่อมโยง Issue, Branch และ PR

## ลงมือทำ

1. ใน Repository ตนเองเลือก Issues → New issue ใช้ [แม่แบบงาน](../../examples/templates/issue-task.md) ตั้งชื่อ `Add navigation back to README`
2. ระบุไฟล์ `projects/first-project.md` และเกณฑ์: มีลิงก์กลับ README, กดได้จริง, เนื้อหาเดิมยังอยู่ แล้วบันทึกเลข Issue
3. ใน Desktop เลือก main → Fetch/Pull → New branch เช่น `issue-12-add-navigation` โดยแทน 12 ด้วยเลขจริง
4. เพิ่ม `[Back to home](../README.md)` ใน `projects/first-project.md` เหตุผลที่ใช้ `../` คือไฟล์อยู่ในโฟลเดอร์ projects ต้องย้อนขึ้นหนึ่งระดับ
5. ตรวจลิงก์ใน Markdown Preview และ Diff แล้ว Commit `docs: add navigation to project page` → Publish branch
6. เปิด PR เข้า main ระบุสิ่งที่เปลี่ยน วิธีตรวจ และ `Closes #12` โดยแทนเลขให้ถูกต้อง
7. ให้เพื่อน Review และคลิกลิงก์จากไฟล์ใน Branch นี้ หากต้องแก้ให้ Commit/Push เพิ่มบน Branch เดิม
8. เมื่อผ่านเกณฑ์แล้ว Merge เข้า main ตรวจว่า Issue เปลี่ยนเป็น Closed และมีลิงก์ PR ที่เกี่ยวข้อง ถ้ายังไม่ปิด ให้ตรวจเลข ตำแหน่ง keyword และ Base/default branch ก่อนปิดเอง
9. กลับ Desktop → main → Fetch/Pull ตรวจลิงก์และ Changes ว่าง สรุปใน Learning log ผ่าน Branch/PR ใหม่หากจะบันทึกเพิ่ม

## Checkpoint

- [ ] Issue มีปัญหาและเกณฑ์ตรวจรับที่ชัดเจน
- [ ] PR เชื่อม Issue จริงและมี Review จากเพื่อน
- [ ] Issue ปิดหลัง Merge งานเข้า main และ Local main อัปเดตแล้ว

## Mini Challenge · ชิ้นงานปลายทาง

เลือกปรับปรุงอีกหนึ่งเรื่องที่ยังไม่ได้ทำ เช่น เพิ่มวิธีเปิดอ่านโปรเจกต์ เพิ่ม Learning goals หรือเพิ่มหน้าผลงานอีกหน้า เปิด Issue และทำ Workflow ครบโดยใช้ [ใบงานชิ้นงานปลายทาง](../../worksheets/final-project.md)

## คำถามทบทวน

1. Issue กับ Pull Request ตอบคำถามต่างกันอย่างไร?
2. ทำไม Acceptance criteria ช่วยให้ Review ตรงกัน?
3. ถ้าใส่ Closes ถูกแต่ Merge เข้า Branch อื่น ทำไม Issue ยังเปิดอยู่?

[ก่อนหน้า](../07-conflicts-and-recovery/README.md) · [ใบงาน 08](../../worksheets/08-issues-and-team-workflow.md) · [ชิ้นงานปลายทาง](../../worksheets/final-project.md) · [สารบัญ](../README.md)
