# Command-Line Track · Git และ GitHub ผ่าน Terminal

เส้นทางสำหรับผู้อ่านที่ต้องการใช้คำสั่งเป็นหลัก เรียนผ่านโปรเจกต์เดียวชื่อ `my-first-project-cli` ตั้งแต่การตั้งค่า การจัด Commit ไปจนถึง Review และปิด Issue ใช้คำอธิบายภาษาไทยและชื่อคำสั่งภาษาอังกฤษให้สอดคล้องกับหลักสูตรเดิม

## เลือกเส้นทางให้เหมาะกับตนเอง

| เส้นทาง | เครื่องมือ | เหมาะกับ |
|---|---|---|
| [Desktop และเว็บไซต์](../README.md) | GitHub Desktop, editor, browser | ผู้เริ่มต้นที่ชอบหน้าต่างโปรแกรม |
| **Command Line ชุดนี้** | Git, Terminal, editor และ GitHub CLI (`gh`) | ผู้ที่ต้องการฝึก Workflow ด้วยคำสั่ง |
| Git CLI ร่วมกับเว็บไซต์ | Git/Terminal สำหรับงาน Git และเว็บสำหรับ Issue/PR | ผู้ที่ยังไม่ติดตั้ง gh |

Git ใช้จัดการ Repository ส่วน `gh` ใช้บริการ GitHub เช่น สร้าง Repository, Issue และ PR การติดตั้ง Git ไม่ได้ติดตั้ง gh ตามไปด้วย สามารถเรียนชุดนี้โดยไม่เคยใช้ Desktop มาก่อน แต่ควรเข้าใจ [แนวคิด Git/GitHub](../01-git-and-github/README.md)

## สารบัญ

| บท | เนื้อหา | กิจกรรมหลัก |
|---|---|---|
| [CLI-01](01-setup/README.md) | Terminal, Git, identity, authentication | ตั้งค่าและตรวจเครื่องมือ/บัญชี |
| [CLI-02](02-repositories/README.md) | init, clone, remote, publish | สร้างโปรเจกต์และส่งขึ้น GitHub |
| [CLI-03](03-staging-and-commits/README.md) | status, diff, staging, history, ignore | แยกสิ่งที่ Save/Stage/Commit |
| [CLI-04](04-branches-and-merges/README.md) | switch, branch, merge, graph | แยกงานและทดลอง Merge บน Branch ฝึก |
| [CLI-05](05-sync-and-remotes/README.md) | fetch, pull, push, tracking, divergence | ส่งรับข้อมูลและแก้ Push rejection |
| [CLI-06](06-pull-requests/README.md) | gh pr create/view/diff/review/merge | จับคู่ Review ผ่าน Terminal |
| [CLI-07](07-conflicts-and-recovery/README.md) | conflict, merge --abort, restore, revert | สร้าง Conflict และย้อนงานโดยคงประวัติ |
| [CLI-08](08-issues-and-teamwork/README.md) | gh issue, PR linkage, team workflow | ทำงานตั้งแต่ Issue จนปิดงาน |

แต่ละบทมีเป้าหมาย เหตุผลของคำสั่ง ขั้นตอน Checkpoint และ Mini Challenge ไม่มีการกำหนดนาทีต่อหัวข้อ [ใบงาน CLI](../../worksheets/command-line/README.md) ใช้คู่กับการเรียน

## ข้อตกลงการใช้คำสั่ง

- ตัวอย่าง Shell ใช้ **Bash**: Windows เปิด Git Bash, macOS ใช้ Terminal (ตัวอย่างใช้ได้ใน zsh เช่นกัน), Linux ใช้ Bash หากใช้ PowerShell ให้ใช้คำสั่ง Git เดียวกัน แต่ปรับคำสั่งสร้างไฟล์/ตัวแปรตาม Shell
- ไม่พิมพ์ `$` หรือ `>` นำหน้าคำสั่ง คำว่า `OWNER`, `PR_NUMBER`, `ISSUE_NUMBER` และ `COMMIT_SHA` คือค่าที่ต้องแทนเอง ไม่ใช่ข้อความที่จะใช้จริง
- `printf '...' > file` เขียนทับไฟล์ จึงใช้เฉพาะไฟล์ใหม่หรือไฟล์ฝึกตามบท `>>` ต่อท้ายไฟล์ อ่านคำอธิบายก่อน Copy ทั้งบล็อก
- คำสั่งที่ตามด้วย “แก้ไฟล์แล้ว” ต้องหยุดไปแก้และ Save ก่อน ไม่รันบล็อกถัดไปทันที
- ถ้า `git log` หรือ `git diff` เปิดตัวอ่านแบบเลื่อนหน้า กด `q` เพื่อออก
- ทำใน Repository ฝึกที่ไม่มีข้อมูลลับ ตรวจ `git status` และชื่อ Branch ก่อนเขียนงาน ไม่ใส่ Token ใน URL หรือใบงาน
- ใช้ Repository CLI ใหม่หากเคยเรียน Desktop แล้ว เพื่อให้ชื่อ Branch และกิจกรรมไม่ชนกับงานเดิม เลือกทำเส้นทางหลักครั้งเดียว ไม่ทำ init ซ้ำในโฟลเดอร์ที่ Clone แล้ว

## จุดตรวจประจำวัน

```bash
git rev-parse --show-toplevel
git status --short --branch
git remote -v
```

คำสั่งแรกต้องรันภายใน Git Repository หากยังไม่ init/clone จะเกิดข้อความ not a git repository ซึ่งไม่ใช่ปัญหาการติดตั้ง

[แก้ปัญหา CLI](troubleshooting.md) · [เอกสารต้นฉบับ](references.md)

[เริ่ม CLI-01](01-setup/README.md) · [คำสั่งย่อ](../../appendix/command-line.md) · [ผู้สอน](../../instructor/command-line-guide.md) · [กลับหน้าหลัก](../../README.md)
