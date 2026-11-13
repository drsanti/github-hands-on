# GitHub Hands-On: A Practical Guide for Beginners

เรียนรู้ GitHub ผ่านการลงมือทำ ด้วย **GitHub Desktop** และ **เว็บไซต์ GitHub**

A beginner-friendly workshop covering repositories, commits, branches, pull requests, and collaboration. The core activities require no command-line commands.

## แนวทางการเรียนรู้

- กลุ่มเป้าหมาย: ผู้เริ่มต้น ไม่จำเป็นต้องมีประสบการณ์ Git
- ระยะเวลาแนะนำ: 4 ชั่วโมง (240 นาที ไม่รวมพักและติดตั้งเครื่องมือ)
- สัดส่วนเวลา: อธิบายและสาธิต 25% / ลงมือทำ 65% / สรุปและสะท้อนผล 10%
- โปรเจกต์ฝึก: สร้าง `my-first-project` สำหรับแนะนำตัวและรวบรวมผลงาน แล้วทำงานร่วมกับเพื่อน
- สถานะเอกสาร: โครงสร้างหลักสูตรเบื้องต้น บทเรียนและใบงานแบบละเอียดจะเพิ่มเติมภายหลัง

## เครื่องมือ

| เครื่องมือ | ใช้ทำอะไร |
|---|---|
| GitHub website | สร้าง Repository, จัดการ Issues, เปิดและ Review Pull Requests, Merge |
| GitHub Desktop | Clone, ตรวจสอบการเปลี่ยนแปลง, Commit, Push, Fetch/Pull, สร้างและสลับ Branch |
| โปรแกรมแก้ไขข้อความ เช่น VS Code | แก้ README, เขียนเนื้อหา และจัดการไฟล์โปรเจกต์ |

เตรียมบัญชี GitHub, ติดตั้ง GitHub Desktop บนระบบที่รองรับ และเตรียมโปรแกรมแก้ไขข้อความก่อนเรียน ผู้ที่ใช้เครื่องซึ่งไม่รองรับ Desktop สามารถเริ่มจากกิจกรรมบนเว็บไซต์ได้ ส่วนคำสั่ง Terminal เป็นเนื้อหาเสริม

## โครงสร้างบทเรียน

| บท | หัวข้อหลัก | หัวข้อย่อย | กิจกรรมและ Checkpoint |
|---|---|---|---|
| 01 | เข้าใจ Git และ GitHub | Version control, Local/Remote, Repository, Commit, Branch | สำรวจ Repository และประวัติการแก้ไข อธิบายบทบาท Git และ GitHub |
| 02 | สร้าง Repository แรก | Public/Private, README, โครงสร้างไฟล์ | สร้าง `my-first-project` และ README แนะนำตัว เปิดลิงก์ Repository ได้ |
| 03 | แก้ไขไฟล์และบันทึกประวัติ | Markdown, เพิ่ม/แก้ไข/ลบไฟล์, Commit message, History, Diff | เพิ่ม About Me, Skills และ Project Ideas พร้อมอย่างน้อย 3 Commits และอ่าน Diff |
| 04 | ทำงานจากคอมพิวเตอร์ | GitHub Desktop, Clone, Local changes, Commit, Push, Fetch, Pull | Clone → แก้ไฟล์ → Commit → Push จากนั้นแก้บนเว็บและ Pull กลับเครื่อง |
| 05 | ใช้ Branch ทดลองเปลี่ยนแปลง | main, Feature branch, การสลับ Branch | สร้าง `add-project-page` เพิ่มหน้าโปรเจกต์และ Commit โดย main ยังไม่เปลี่ยน |
| 06 | ทำงานร่วมกันด้วย Pull Request | Collaborator, Pull Request, Review, Comment, Merge | จับคู่ทำงานใน Repository ที่ให้สิทธิ์แล้ว เพื่อนเปิด PR เจ้าของตรวจและ Merge |
| 07 | แก้ปัญหาและกู้คืนงาน | Merge conflict, การเลือกเนื้อหา, Revert | สร้าง Conflict จากสอง Branch ที่แก้บรรทัดเดียวกัน แก้และตรวจผล จากนั้นฝึก Revert Commit ที่ Push แล้ว |
| 08 | จัดการงานและสรุปโปรเจกต์ | Issues, เกณฑ์สำเร็จ, เชื่อม PR กับ Issue, ข้อมูลลับ | Issue → Branch → Commit → PR → Review → Merge → ปิด Issue |

## รูปแบบของแต่ละบท

1. **เป้าหมาย:** ระบุสิ่งที่ผู้เรียนจะทำได้ 1–2 ข้อ
2. **สถานการณ์:** เริ่มจากปัญหาหรือความต้องการที่พบจริง
3. **แนวคิดที่จำเป็น:** อธิบายคำศัพท์พร้อมตัวอย่างเท่าที่ต้องใช้
4. **Demo:** ผู้สอนสาธิตขั้นตอนสั้น ๆ
5. **ลงมือทำ:** กำหนดขั้นตอน ชื่อไฟล์ และข้อความตัวอย่าง
6. **Checkpoint:** ระบุผลที่ต้องเห็นในเครื่องหรือบน GitHub
7. **Mini Challenge:** ให้ฝึกด้วยตนเองจากสถานการณ์ใหม่
8. **คำถามทบทวน:** ให้ผู้เรียนอธิบายเหตุผล เช่น Commit แล้วทำไมเพื่อนยังไม่เห็นไฟล์?

## Workflow ที่ฝึกซ้ำ

1. Clone Repository ด้วย GitHub Desktop
2. สร้าง Branch สำหรับงานใหม่
3. แก้ไขไฟล์ด้วยโปรแกรมแก้ไขข้อความ
4. ตรวจ Diff และ Commit ใน GitHub Desktop
5. Push หรือ Publish Branch ไป GitHub
6. เปิด Pull Request บนเว็บไซต์ GitHub
7. ให้เพื่อน Review แล้ว Merge
8. กลับมาที่ main ใน Desktop และ Pull งานล่าสุด

## ชิ้นงานปลายทาง

ส่งลิงก์ Repository เดียว พร้อมหลักฐานต่อไปนี้:

- README อธิบายโปรเจกต์และมีรูปภาพที่ผู้เรียนมีสิทธิ์ใช้งาน
- Commit history ที่มีข้อความสื่อความหมาย
- Pull Request ที่ผ่าน Review และ Merge
- ความคิดเห็นจากการ Review ของเพื่อน
- Issue ที่เชื่อมกับงานที่ทำสำเร็จ
- อธิบายความแตกต่างระหว่าง Commit, Push และ Pull ได้

ใช้ไฟล์ฝึกที่ไม่มีรหัสผ่าน API keys หรือข้อมูลส่วนบุคคล เลือก Public/Private ให้เหมาะสม และตรวจ Diff ก่อน Commit ทุกครั้ง

## รูปแบบย่อ 2 ชั่วโมง

เน้นบท 01–03 และ 05–06 ผ่านเว็บไซต์ GitHub โดยปรับเวลาสาธิตและแบบฝึกให้เหมาะสม จัดการทำงานบนเครื่อง การแก้ Conflict และ Issues เป็นครั้งถัดไป

## โครงสร้างเอกสารที่วางแผนไว้

| ตำแหน่ง | เนื้อหา |
|---|---|
| `README.md` | ภาพรวมหลักสูตรและเส้นทางการเรียนรู้ |
| `lessons/` | บทเรียน 01–08 |
| `worksheets/` | ใบงานและ Checkpoints |
| `examples/` | ตัวอย่าง README และไฟล์สำหรับฝึก |
| `assets/` | ภาพประกอบและภาพหน้าจอ |
| `instructor/` | แนวทางสอน เฉลย และเกณฑ์ประเมิน |
| `appendix/` | คำศัพท์และคำสั่ง Git ทางเลือก |

ตารางนี้เป็นแผนโครงสร้างโฟลเดอร์ ยังไม่ได้สร้างไฟล์บทเรียนทั้งหมด
