# CLI-01 · เครื่องมือ Identity และ Authentication

## เป้าหมายและสถานการณ์

เตรียม Terminal ให้ใช้ Git ได้ และแยกให้ได้ว่า “ใครเขียน Commit” กับ “บัญชีใดมีสิทธิ์เข้า GitHub” เป็นคนละเรื่อง ไม่จำเป็นต้องติดตั้ง Desktop

## เตรียมเครื่องมือ

ติดตั้ง Git จาก [แหล่งทางการ](https://git-scm.com/install/) และ GitHub CLI จาก [cli.github.com](https://cli.github.com/) ตามระบบปฏิบัติการ เปิด Terminal ใหม่หลังติดตั้ง Windows ใช้ Git Bash เพื่อให้คำสั่งสร้างไฟล์ในบทต่อไปตรงตัวอย่าง

```bash
git --version
gh --version
pwd
```

ใช้ Git 2.28 ขึ้นไปสำหรับ `git init -b main` ในชุดนี้ `pwd` แสดงโฟลเดอร์ปัจจุบัน ถ้าไม่พบ gh ยังฝึก Git แบบ Local ได้ และใช้เว็บไซต์แทนคำสั่ง gh ในบทที่เกี่ยวข้อง

## ลงมือทำ A · ตั้ง Identity

แทนชื่อและอีเมลด้วยค่าของตนเองก่อนรัน ใช้อีเมลที่ยืนยันบน GitHub หรืออีเมล noreply ที่บัญชีแสดงใน Settings → Emails ไม่ Copy อีเมลตัวอย่างไปใช้เป็นของตนเอง

```bash
git config --global user.name "Your Name"
git config --global user.email "your-verified-email@example.com"
git config --global init.defaultBranch main
git config --global --get user.name
git config --global --get user.email
```

`--global` เป็นค่าตั้งต้นสำหรับ Repository ของผู้ใช้บนเครื่องนี้ ถ้าเป็นเครื่องร่วมไม่ควรทับ Identity ของคนอื่น ให้ตั้ง `git config user.name ...` และ `git config user.email ...` แบบไม่ใส่ `--global` หลัง init/clone ในบท 02 ก่อน Commit แรกแทน Git ใช้ Identity ประกอบ Commit ไม่ได้ใช้แทนการ Login

## ลงมือทำ B · เข้าสู่ GitHub ด้วย HTTPS

สำหรับเส้นทางใช้ gh ร่วมกับ Git:

```bash
gh auth login --hostname github.com --git-protocol https --web
gh auth status --hostname github.com
gh auth setup-git --hostname github.com
```

ทำตามขั้นตอน Login ในเบราว์เซอร์ที่ gh เปิดให้ ตรวจชื่อบัญชีและสิทธิ์ที่ขอก่อนยืนยัน `setup-git` ตั้งให้ Git ใช้ gh ช่วยจัดการข้อมูลยืนยันตัวตน ไม่เปลี่ยนผู้เขียน Commit

ถ้าเครื่องใช้ Credential Manager หรือ SSH ที่ตั้งไว้แล้วและใช้งานได้ ไม่จำเป็นต้องเปลี่ยนเป็น gh helper ให้ใช้ระบบเดิมและบันทึกวิธีที่เลือก Password บัญชี GitHub ไม่ใช้แทน Token สำหรับ Git ผ่าน HTTPS [ดู Authentication](https://docs.github.com/en/get-started/git-basics/about-remote-repositories)

ไม่ใช้ `gh auth token` เพื่อเก็บหลักฐาน และไม่ส่งหน้าจอที่มี Token หาก gh แจ้งว่าเก็บ Credential แบบข้อความธรรมดา ให้ตรวจวิธีตั้ง Credential store ที่ระบบรองรับ โดยเฉพาะเครื่องร่วม

## Demo และ Checkpoint

ผู้สอนแสดง Version, Identity และชื่อบัญชี โดยไม่แสดง Secret

- [ ] Git เรียกใช้ได้ และรู้ว่ากำลังใช้ Shell อะไร
- [ ] ระบุ Identity ของ Commit และบัญชีที่ Login แยกกันได้
- [ ] gh Login สำเร็จ หรือระบุทางเลือก Credential/เว็บไซต์ที่ใช้

## Mini Challenge และทบทวน

อธิบายว่าเปลี่ยน `user.name` เป็นชื่อเพื่อนแล้วทำไมยัง Push เข้า Repository ของเพื่อนไม่ได้ จากนั้นค้น `git help config` หรือ `git config -h` แล้วหาความต่าง local/global

[ใบงาน](../../../worksheets/command-line/01-setup.md) · [ถัดไป](../02-repositories/README.md) · [สารบัญ](../README.md)
