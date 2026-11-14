# คู่มือผู้สอน · Command-Line Track

## เป้าหมายการสอน

ใช้ [บท CLI-01 ถึง CLI-08](../lessons/command-line/README.md) เป็นอีกเส้นทางของหลักสูตร ผู้เรียนควรทายผลก่อนรันคำสั่ง และอธิบายสถานะหลังรันได้ ไม่ประเมินจากการจำ flags เพียงอย่างเดียว

ตั้งชื่อ Repository แยก `my-first-project-cli` เพื่อไม่ชนกับงาน Desktop ใช้ Git Bash บน Windows เพื่อให้คำสั่ง Shell ตรงเอกสาร เตรียม Git 2.28 ขึ้นไป และ gh สำหรับผู้เลือกเส้นทาง GitHub CLI ผู้ที่ไม่ใช้ gh ทำ Git ใน Terminal และ PR/Issue ผ่านเว็บได้

## จุดตรวจและแนวคำตอบรายบท

| บท | หลักฐานที่ควรเห็น | เหตุผลสำคัญ |
|---|---|---|
| 01 | Version, Identity และบัญชี Login | user.name/email ไม่ได้ให้สิทธิ์ GitHub |
| 02 | main มี Commit, origin ถูก และ Push แล้ว | init สร้าง Local; clone รับ Repo เดิม; ไม่ทำสองเส้นทางซ้อนกัน |
| 03 | สถานะ AM และ Diff สองแบบ | Index เก็บเนื้อหาขณะ Add ไม่ติดตาม Save รอบใหม่เอง |
| 04 | main ไม่มีหน้าใหม่ Branch งานมี | Local merge ไม่ต้องมี PR และ Fast-forward ไม่สร้าง Merge commit ใหม่ |
| 05 | Fetch ยังไม่แก้ไฟล์; ff-only หยุดเมื่อ Diverged | อ่าน Graph ก่อนเลือกวิธีรวม ไม่ใช้ Force push แทน Sync |
| 06 | PR Merged, มี Review จากบัญชีอื่น | Git และ gh ทำหน้าที่ต่างกัน Push ไม่เท่ากับเปิด PR |
| 07 | Conflict จริง, markers หาย, Revert ใหม่ | Restore เขียนทับงานยังไม่ Commit ส่วน Revert คงประวัติเดิม |
| 08 | Issue เชื่อม PR และปิดหลัง Merge | ต้องใช้เลขจริงใน description และ default branch |

## จุดที่ต้องเตรียมเป็นพิเศษ

- CLI-03 หยุดหลัง Add แล้วเพิ่มบรรทัดที่ยังไม่ Add ให้นักศึกษาอ่าน `AM` ก่อน Commit
- CLI-04 ทดสอบ Merge บน `merge-practice` แล้วกลับ `add-project-page` ก่อนลบ Branch ฝึก เก็บ Branch งานไว้เปิด PR
- CLI-05 ใช้สอง Clone ไม่ใช้สอง Terminal ในโฟลเดอร์เดียว เพราะสอง Terminal นั้นแชร์ Working tree และไม่ได้จำลองสองสำเนา
- CLI-06 ถ้า main จาก Sync ชนกับ README ของ Branch งาน ให้ช่วยอ่าน Conflict หรือข้ามไปดู CLI-07 แล้วกลับมา ไม่ทิ้งงานเพื่อน
- CLI-07 ใช้ Local `conflict-base`, `title-a`, `title-b`, `conflict-integration` ไม่แก้ main ส่วน Revert ใช้ Branch ที่ Push แยก `practice-revert` และไม่ต้องสร้าง PR ที่ไม่มี Diff
- ไม่ทำ Auth หรือ Online commands แทนนักศึกษาในบัญชีร่วม ให้แต่ละคนรับผิดชอบการ Login และสิทธิ์ของตนเอง

## การประเมิน

ใช้ [เกณฑ์หลัก](assessment.md) ประกอบ โดยแทนหลักฐาน Desktop ด้วย status/diff/log/remote ของงานจริง ให้คะแนนตามพฤติกรรมและเหตุผล ไม่บังคับใช้ Message/SHA ตรงตัวอย่าง ความเข้าใจ Staging และการ Sync ต้องมีหลักฐานจาก Local ส่วน Issue/PR ตรวจจาก GitHub URL ได้

ชิ้นงานยังเป็นเอกสารแนะนำตัวและหน้าโปรเจกต์ ไม่ต้องเขียนโปรแกรม หากต้องการครบเกณฑ์ภาพประกอบ ให้นำ [ภาพตัวอย่าง](../assets/images/project-icon.svg) ไปเพิ่มใน assets ของโปรเจกต์แล้ว Commit ด้วย CLI ตามคำอธิบายเพิ่มเติมใน CLI-03

ถามผู้เรียนก่อนสรุป: “ตอนนี้อยู่ Repo ไหน Branch ไหน และงานนี้ยังอยู่ใน Working tree, Index, Local commit หรือ Remote แล้ว?”

[สารบัญผู้สอน](README.md) · [ใบงาน CLI](../worksheets/command-line/README.md)
