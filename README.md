# GitHub Hands-On: A Practical Guide for Beginners

เรียนรู้ GitHub ผ่านการลงมือทำ เลือก **Desktop/เว็บไซต์** หรือ **Command Line**

สร้างโปรเจกต์แนะนำตัวและผลงานตั้งแต่ Repository แรก จนถึงการทำงานร่วมกับเพื่อนด้วย Pull Request เส้นทาง Desktop/เว็บไซต์ไม่ต้องใช้ Command Line ส่วนเส้นทาง CLI ใช้ Git และ GitHub CLI (`gh`) เป็นหลัก ทั้งสองเส้นทางไม่จำเป็นต้องเขียนโปรแกรมเป็น

## เลือกเส้นทางการเรียน

| เส้นทาง | เริ่มต้น | พื้นที่ฝึก |
|---|---|---|
| Desktop และเว็บไซต์ | [บทเรียนเดิม 01–08](lessons/README.md) | `my-first-project` |
| Command Line | [CLI-01 ถึง CLI-08](lessons/command-line/README.md) | `my-first-project-cli` |

เลือกเรียนเส้นทางเดียวได้ หรือเรียนอีกเส้นทางเพื่อเปรียบเทียบเครื่องมือ ใช้ [ใบงาน CLI](worksheets/command-line/README.md) สำหรับกลุ่ม Terminal

## เริ่มเรียนเส้นทาง Desktop/เว็บไซต์

1. อ่าน [เตรียมความพร้อม](docs/getting-started.md) และติดตั้งเครื่องมือ
2. เรียนตาม [บทเรียน 01–08](lessons/README.md) โดยใช้ Repository ฝึกของตนเองต่อเนื่องกัน
3. บันทึกผลใน [ใบงาน](worksheets/README.md) และส่ง [ชิ้นงานปลายทาง](worksheets/final-project.md)

Repository นี้คือ **เอกสารประกอบการเรียน** ส่วน `my-first-project` คือ **พื้นที่ฝึกของผู้เรียน** ให้ทำกิจกรรมในพื้นที่ฝึกของตนเอง ไม่แก้เอกสารหลักสูตรเพื่อส่งงาน

## เครื่องมือและหน้าที่

| เครื่องมือ | หน้าที่ |
|---|---|
| เว็บไซต์ GitHub | สร้าง Repository, แก้ไฟล์เบื้องต้น, Issues, Pull Requests, Review และ Merge |
| GitHub Desktop | Clone, ตรวจ Diff, Commit, Push, Fetch/Pull และจัดการ Branch บนเครื่อง |
| โปรแกรมแก้ไขข้อความ เช่น VS Code | แก้ Markdown และไฟล์โปรเจกต์ |

ใช้ Desktop เป็นเครื่องมือหลักตั้งแต่บท 04 ส่วนคำสั่ง Git อยู่ใน [ภาคผนวกทางเลือก](appendix/command-line.md) ผู้ใช้ระบบที่ไม่รองรับ Desktop ดู [เส้นทางผ่านเว็บ](docs/getting-started.md#เรียนผ่านเว็บไซต์อย่างเดียว)

## โครงสร้างบทเรียน Desktop/เว็บไซต์

| บท | หัวข้อหลักและหัวข้อย่อย | กิจกรรมสำคัญ |
|---|---|---|
| [01](lessons/01-git-and-github/README.md) | Git/GitHub, Repository, Local/Remote, Commit และ Branch | สำรวจไฟล์และประวัติใน Repository |
| [02](lessons/02-first-repository/README.md) | สร้าง Repository, Public/Private, README | สร้าง `my-first-project` พร้อม README |
| [03](lessons/03-files-and-commits/README.md) | Markdown, ไฟล์/โฟลเดอร์, Commit message, History และ Diff | แก้เอกสารและอ่านการเปลี่ยนแปลง |
| [04](lessons/04-github-desktop/README.md) | Clone, Edit, Commit, Push, Fetch และ Pull | ส่งและรับงานระหว่างเครื่องกับ GitHub |
| [05](lessons/05-branches/README.md) | main, Feature branch, Publish branch | เพิ่มหน้าโปรเจกต์บน Branch แยก |
| [06](lessons/06-pull-requests/README.md) | Collaborator, PR, Review, Comment และ Merge | จับคู่ตรวจงานและรวมการเปลี่ยนแปลง |
| [07](lessons/07-conflicts-and-recovery/README.md) | Merge conflict, วิธีตัดสินใจแก้เนื้อหา, Revert | สร้าง Conflict ที่ควบคุมได้และกู้คืนงาน |
| [08](lessons/08-issues-and-team-workflow/README.md) | Issues, Acceptance criteria, PR linkage | ทำงานครบวงจรจาก Issue จนปิดงาน |

แต่ละบทมีเป้าหมาย สถานการณ์ แนวคิด Demo ขั้นตอนลงมือทำ Checkpoint, Mini Challenge และคำถามทบทวน ให้ผ่าน Checkpoint ก่อนเริ่มบทถัดไป

## โครงสร้างไฟล์และโฟลเดอร์

| ตำแหน่ง | เนื้อหา |
|---|---|
| [docs/](docs/README.md) | การเตรียมเครื่อง แผนผังเอกสาร และเอกสารอ้างอิง |
| [lessons/](lessons/README.md) | บทเรียน Desktop/เว็บไซต์ 01–08 |
| [lessons/command-line/](lessons/command-line/README.md) | บทเรียน CLI-01 ถึง CLI-08 พร้อมการแก้ปัญหาและอ้างอิง |
| [worksheets/command-line/](worksheets/command-line/README.md) | ใบงานปฏิบัติสำหรับผู้ใช้ Terminal |
| [worksheets/](worksheets/README.md) | ใบงานบันทึกหลักฐานรายบทและชิ้นงานปลายทาง |
| [examples/](examples/README.md) | Starter project, ไฟล์ฝึก Conflict และแม่แบบ Issue/PR |
| [assets/](assets/README.md) | ตัวอย่างภาพประกอบและแนวทางจัดเก็บภาพ |
| [instructor/](instructor/README.md) | คู่มือสอน แนวคำตอบ และเกณฑ์ประเมิน |
| [appendix/](appendix/README.md) | คำศัพท์ การแก้ปัญหา และ Command Line ทางเลือก |
| [CONTRIBUTING.md](CONTRIBUTING.md) | แนวทางปรับปรุงเอกสารหลักสูตร |

## ชิ้นงานที่ผู้เรียนจะได้

- Repository แนะนำตัวพร้อม README, รูปภาพ และหน้าโปรเจกต์
- Commit history ที่อธิบายการเปลี่ยนแปลงได้
- Pull Request ที่มีข้อคิดเห็นจากเพื่อนและ Merge สำเร็จ
- หลักฐานแก้ Conflict และ Revert โดยยังอ่านประวัติได้
- Issue ที่เชื่อมกับ PR และปิดเมื่อทำงานเสร็จ

เน้นลงมือทำเป็นหลัก ให้ผู้สอนสาธิตหนึ่งรอบ แล้วผู้เรียนทำเองและอธิบายผล หัวข้อ เวลา และระดับความช่วยเหลือสามารถปรับตามกลุ่มผู้เรียน

ชื่อเมนูอาจต่างกันตามเวอร์ชัน ให้ยึดหน้าที่ของคำสั่งประกอบกับ [เอกสาร GitHub ต้นฉบับ](docs/references.md)
