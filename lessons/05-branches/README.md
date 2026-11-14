# บท 05 · ทดลองเปลี่ยนแปลงด้วย Branch

## เป้าหมาย

สร้าง Branch จาก `main` และพิสูจน์ได้ว่าการเปลี่ยนแปลงยังไม่ถูกรวมเข้า `main`

## สถานการณ์

ต้องการเพิ่มหน้าโปรเจกต์ให้เพื่อนตรวจก่อนรวมเข้าหน้าหลัก จึงแยกงานใน `add-project-page`

## แนวคิดที่ต้องใช้

Branch ช่วยแยกเส้นทาง Commits ไม่ใช่การสร้างโฟลเดอร์โปรเจกต์อีกชุด การสลับ Branch ทำให้ไฟล์ที่เห็นเปลี่ยนตาม Commit ของ Branch นั้น งานที่ Save แต่ยังไม่ Commit อาจติดไปเมื่อสลับ Branch หรือทำให้โปรแกรมขอจัดการงานค้าง จึงควร Commit งานให้เรียบร้อยก่อนสลับ

## Demo โดยผู้สอน

สร้าง Branch เพิ่มไฟล์แล้ว Commit สลับกลับ main เพื่อแสดงว่าไฟล์นั้นยังไม่อยู่ใน main จากนั้นสลับกลับ Branch งาน

## ลงมือทำ

1. ใน Desktop เลือก `my-first-project` → Current Branch → main ตรวจ Changes ว่าง แล้ว Fetch/Pull ให้ล่าสุด
2. เลือก Branch → New branch ตั้งชื่อ `add-project-page` ตรวจว่าเริ่มจาก `main` แล้ว Create branch
3. ในโปรแกรมแก้ไขสร้างโฟลเดอร์ `projects` และไฟล์ `projects/first-project.md` ใช้ตัวอย่าง:

```markdown
# My First Project Idea

## Problem
ต้องการรวบรวมผลงานที่ค้นหาและอ่านได้ง่าย

## Proposed Solution
จัดหน้าแนะนำผลงานใน GitHub และเชื่อมจาก README

## Expected Result
ผู้อ่านเปิดหน้าโปรเจกต์จาก README ได้
```

4. เพิ่ม `[First project](projects/first-project.md)` ใน README และลองเปิดลิงก์ใน Preview
5. ตรวจ Diff ใน Desktop แล้ว Commit `docs: add first project page`
6. สลับกลับ `main` ตรวจว่าไม่มีไฟล์ใหม่และลิงก์นี้ จากนั้นกลับ `add-project-page` ตรวจว่ากลับมา
7. เลือก Publish branch เพื่อส่ง Branch ขึ้น GitHub ถ้า Publish แล้ว ปุ่มส่งงานครั้งต่อไปคือ Push origin
8. เปิดเว็บ เลือก Branch `add-project-page` ตรวจไฟล์ แล้วเปลี่ยนไป `main` เปรียบเทียบ ทั้งสองยังต่างกัน

**จบบทนี้ให้เก็บ Branch ไว้ ยังไม่ Merge** จะนำไปเปิด PR ในบท 06

## Checkpoint

- [ ] มี Branch `add-project-page` ทั้งเครื่องและ GitHub
- [ ] ไฟล์ใหม่แสดงใน Branch งาน แต่ยังไม่อยู่ใน main
- [ ] ไม่มีงานค้างและรู้ว่ากำลังอยู่ Branch ไหน

## Mini Challenge

เพิ่มหัวข้อ `Next Steps` ในหน้าโปรเจกต์ Commit และ Push อีกครั้งบน Branch เดิม ตรวจว่า main ยังไม่เปลี่ยน

## คำถามทบทวน

1. Publish branch ต่างจาก Merge อย่างไร?
2. ถ้าสร้าง Branch จาก Branch ที่ผิด งานอะไรอาจติดไปด้วย?
3. ทำไมควรสร้าง Branch จาก main ที่ Pull ล่าสุดแล้ว?

[ก่อนหน้า](../04-github-desktop/README.md) · [ใบงาน 05](../../worksheets/05-branches.md) · [ถัดไป: บท 06](../06-pull-requests/README.md)
