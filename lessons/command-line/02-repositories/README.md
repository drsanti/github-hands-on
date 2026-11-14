# CLI-02 · สร้าง Clone และ Publish Repository

## เป้าหมายและแนวคิด

สร้าง Local repository และเชื่อม GitHub ได้ `git init` เริ่มประวัติในโฟลเดอร์บนเครื่อง `git clone` รับ Repository ที่มีอยู่แล้ว ส่วน `git remote` จัดการที่อยู่ติดต่อ ใช้ **เส้นทาง A หรือ B เพียงเส้นทางเดียว** แล้วได้โปรเจกต์ฝึกเดียวกัน

## ลงมือทำ · เส้นทาง A เริ่มจาก Local (แนะนำสำหรับกลุ่ม CLI)

เปิดโฟลเดอร์เก็บงานที่ไม่อยู่ภายใน Repository อื่น ตรวจด้วย `pwd` แล้วสร้างโฟลเดอร์ชื่อใหม่ ถ้ามีอยู่แล้วให้หยุดและเลือกชื่ออื่น อย่าใช้ไฟล์จริงที่มีอยู่เป็นตัวทดลอง

```bash
mkdir my-first-project-cli
cd my-first-project-cli
git init -b main
printf '# My First Project\n\nLearning Git and GitHub from the command line.\n' > README.md
git status
git add README.md
git diff --staged
git commit -m "docs: create project README"
```

หากเลือก Identity แบบราย Repository ใน CLI-01 ให้ตั้งก่อนคำสั่ง Commit ถ้า Commit ไม่สำเร็จ ให้แก้ Identity แล้วรัน Commit อีกครั้ง ไม่ต้อง init ใหม่

สร้าง GitHub Repository จากโฟลเดอร์นี้และ Push ด้วย gh:

```bash
gh repo create my-first-project-cli --private --source=. --remote=origin --push
git remote -v
git branch -vv
```

`--private` จำกัดผู้อ่าน เหมาะกับพื้นที่ฝึกเริ่มต้น ถ้าต้องการเผยแพร่และตรวจแล้วว่าไม่มีข้อมูลส่วนตัว เปลี่ยนเป็น `--public` **ก่อนรัน** ชื่อเจ้าของเริ่มต้นคือบัญชี gh ที่ Login หากชื่อมีอยู่แล้ว ให้ใช้ชื่อใหม่อย่างสอดคล้องกันตลอดกิจกรรม

ไม่มี gh: สร้าง Repository ว่างบนเว็บโดย **ไม่เพิ่ม README, License หรือ .gitignore** แล้วแทน OWNER ในคำสั่งต่อไปนี้ ใช้วิธียืนยันตัวตน HTTPS ที่ตั้งไว้แล้ว:

```bash
git remote add origin https://github.com/OWNER/my-first-project-cli.git
git push -u origin main
```

ใช้บล็อกนี้เฉพาะเมื่อยังไม่ได้สร้าง origin ด้วย gh หากพบ remote origin already exists ให้ตรวจ `git remote -v` แทนการ Add ซ้ำ

## เส้นทาง B · เริ่มจาก Repository ที่มีอยู่แล้ว

ใช้เมื่อสร้าง Repository บน GitHub พร้อม README แล้ว จึง Clone แทน init ในโฟลเดอร์เดิม แทน OWNER ด้วยบัญชีจริง:

```bash
git clone https://github.com/OWNER/my-first-project-cli.git
cd my-first-project-cli
git status
git branch --show-current
git remote -v
```

ตรวจว่า default branch ชื่อ main หากต่างให้ตกลงชื่อกับผู้สอนและใช้ชื่อนั้นแทนอย่างสอดคล้องกัน อย่าสร้าง Repository ว่างที่ไม่มี Commit แล้วคาดว่าจะเห็น Branch และ README ครบเหมือนตัวอย่าง

## Demo และ Checkpoint

ผู้สอนชี้ความต่างของโฟลเดอร์ธรรมดาก่อน init และ Repository หลัง Commit แล้วเปิดดู Remote

- [ ] มี README และอย่างน้อยหนึ่ง Commit บน main
- [ ] `git status` สะอาด และ `git remote -v` แสดง origin ถูก Repository
- [ ] เปิด Repository บน GitHub แล้วเห็น Commit ของตน หากใช้ Private ให้สิทธิ์คู่ฝึก/ผู้สอนก่อนตรวจ

## Mini Challenge และทบทวน

จากโฟลเดอร์เก็บงานอีกแห่ง Clone Repository นี้เป็น `my-first-project-cli-copy` ด้วย `git clone URL my-first-project-cli-copy` เปิด History เปรียบเทียบ แล้วกลับมาทำบทถัดไปในสำเนาหลัก อธิบายว่า Clone ต่างจาก Copy เฉพาะ README อย่างไร

[ก่อนหน้า](../01-setup/README.md) · [ใบงาน](../../../worksheets/command-line/02-repositories.md) · [ถัดไป](../03-staging-and-commits/README.md)
