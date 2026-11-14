# บท 06 · Pull Request และการทำงานกับเพื่อน

## เป้าหมาย

เปิด PR ตรวจ Base/Compare ให้ถูก Review พร้อมเหตุผล และ Merge แล้วรับงานกลับเครื่องได้

## สถานการณ์

หน้าโปรเจกต์พร้อมแล้ว ต้องให้เพื่อนตรวจความชัดเจนและลิงก์ก่อนรวมเข้าหน้าหลัก

## แนวคิดที่ต้องใช้

- PR เสนอให้รวมงานจาก Compare branch ไป Base branch การ Push เฉย ๆ ยังไม่ Merge
- Review มี Comment, Approve และ Request changes ผู้เขียน PR อนุมัติ PR ของตนเองไม่ได้
- ข้อคิดเห็นที่ดีระบุจุด ปัญหา และสิ่งที่อยากให้ปรับ เช่น “หัวข้อ Expected Result ยังวัดไม่ได้ ช่วยระบุว่าผู้อ่านต้องเปิดลิงก์ใดได้”
- ใน Repository ฝึกที่ไม่มี Branch protection การ Review เป็นข้อตกลงของชั้นเรียน ไม่ได้หมายความว่าระบบจะบังคับรอ Approve

## เตรียมคู่ฝึก

ให้ A และ B ต่างมี Repository ของตนเอง เชิญกันผ่าน Repository → Settings → Collaborators หรือ Manage access → Add people เลือกบัญชีเพื่อนให้ถูกและให้อีกฝ่ายรับคำเชิญ หากเป็น Private ผู้สอนต้องมีสิทธิ์อ่านเพื่อตรวจงาน

การเชิญ Collaborator ให้สิทธิ์เข้าถึงและแก้ Repository จึงใช้เฉพาะพื้นที่ฝึกที่ไม่มีข้อมูลลับ คู่ที่ไม่สะดวกให้สิทธิ์ใช้ [Fork workflow](../../appendix/fork-workflow.md) โดยยังใช้ Desktop ได้

## Demo โดยผู้สอน

แสดง PR ที่ Base ผิดแล้วแก้ให้ถูก เปิด Files changed และเขียน Comment หนึ่งจุดก่อน Review

## ลงมือทำ A · ส่ง Branch จากบท 05

1. เจ้าของ Repository เปิด Pull requests → New pull request
2. ตั้ง Base เป็น `main` และ Compare เป็น `add-project-page` ตรวจรายชื่อไฟล์และ Diff
3. ตั้งชื่อ `Add first project page` และใช้ [แม่แบบ PR](../../examples/templates/pull-request.md) อธิบายสิ่งที่เปลี่ยน เหตุผล และสิ่งที่ตรวจแล้ว
4. เลือก Create pull request แล้วให้เพื่อนเข้าลิงก์ PR หรือเลือกเพื่อนใน Reviewers หากมีสิทธิ์และเมนูนี้ปรากฏ
5. เพื่อนเปิด Files changed อ่านเนื้อหาและทดลองลิงก์จากไฟล์ใน Branch งาน ระบุข้อเสนอแนะอย่างน้อยหนึ่งจุดแล้ว Submit review
6. ผู้เขียนแก้ตามข้อเสนอแนะบน `add-project-page` ในเครื่อง Commit และ Push ไป Branch เดิม PR จะอัปเดตอัตโนมัติ ไม่ต้องเปิด PR ใหม่
7. เพื่อนตรวจรอบใหม่และ Approve เมื่อครบเกณฑ์ เจ้าของตรวจ Base และ Diff อีกครั้ง แล้ว Merge pull request → Confirm merge
8. เจ้าของกลับ Desktop เลือก main → Fetch/Pull ตรวจว่าไฟล์ใหม่เข้ามาและ Changes ว่าง หลังจากนั้นจึงลบ Branch ที่ Merge แล้วได้

## ลงมือทำ B · เพื่อนเป็นผู้ส่งงาน

1. B Clone Repository ของ A ด้วยบัญชีตนเอง หลังรับสิทธิ์ Collaborator แล้ว
2. B เลือก main → Fetch/Pull → สร้าง `improve-learning-log` เพิ่มข้อแนะนำใน `notes/learning-log.md` โดยไม่แก้บรรทัดเดียวกับ A ในกิจกรรมนี้
3. B Commit → Publish branch → เปิด PR เข้า main ของ A
4. A Review ให้ข้อคิดเห็น B ปรับและ Push จากนั้น A ตรวจและ Merge
5. ทั้งคู่กลับ main → Fetch/Pull แล้วสลับบทบาทใน Repository ของ B

## Checkpoint

- [ ] PR มี Base/Compare ถูกต้องและอธิบายสิ่งที่เปลี่ยน
- [ ] มี Review จากอีกคนและหลักฐานปรับตามข้อเสนอแนะ
- [ ] PR แสดง Merged และ main บนเครื่องมีไฟล์ล่าสุด
- [ ] เคยเป็นทั้งผู้เขียน PR และผู้ Review

## Mini Challenge

สร้าง Branch แก้ Learning log หนึ่งเรื่อง ให้คู่ฝึก Review โดยไม่สาธิตซ้ำ อธิบายว่าแต่ละคนทำหน้าที่อะไร

## คำถามทบทวน

1. Pull กับ Pull Request เป็นการกระทำเดียวกันหรือไม่?
2. ทำไมควร Review Files changed ไม่ใช่ดูเพียงชื่อ PR?
3. Merge บนเว็บแล้วทำไมไฟล์บนเครื่องยังไม่เปลี่ยน?

[ก่อนหน้า](../05-branches/README.md) · [ใบงาน 06](../../worksheets/06-pull-requests.md) · [ถัดไป: บท 07](../07-conflicts-and-recovery/README.md)
