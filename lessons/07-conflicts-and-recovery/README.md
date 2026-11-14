# บท 07 · แก้ Conflict และกู้คืนงาน

## เป้าหมาย

สร้าง Conflict จากฐานเดียวกัน แก้เนื้อหาอย่างมีเหตุผล และ Revert Commit ที่ Push แล้วโดยคงประวัติไว้ได้

## สถานการณ์

สอง Branch เปลี่ยนชื่อกิจกรรมในบรรทัดเดียวกัน Git ไม่สามารถตัดสินใจแทนทีมได้ว่าข้อความสุดท้ายควรเป็นอะไร

## แนวคิดที่ต้องใช้

Conflict ไม่ได้หมายความว่าข้อมูลพัง แต่หมายถึงต้องตัดสินใจรวมงานด้วยคน Revert สร้าง Commit ใหม่ที่ย้อนผลของ Commit ที่เลือก ไม่ได้ลบ Commit เก่าจากประวัติ การ Undo งานที่ยังไม่ Commit และการ Revert จึงเป็นคนละเรื่อง

## Demo โดยผู้สอน

เตรียมสอง Branch จาก Commit เดียวกัน แก้บรรทัดเดียวให้ต่างกัน แล้ว Merge ทีละ Branch แสดงว่าทำไม Branch ที่สองขัดกับ main

## ลงมือทำ A · เตรียม Conflict ที่ทำซ้ำได้

ทำใน Repository ฝึกของตนเอง หยุดงานร่วมกันชั่วคราวและเริ่มจาก Changes ว่าง

1. เลือก main → Fetch/Pull สร้างไฟล์ `notes/workshop-title.md` ด้วยข้อความจาก [ไฟล์เริ่มต้น](../../examples/conflict/workshop-title.md):

```markdown
# Workshop Plan

Workshop title: GitHub Basics
```

2. Commit `docs: add base workshop title` และ Push บน main ขั้นตอนนี้เป็นข้อยกเว้นเพื่อเตรียมข้อมูลฝึก
3. จาก main นี้สร้าง `title-a` เปลี่ยนเฉพาะบรรทัดสุดท้ายเป็น `Workshop title: GitHub for Beginners` Commit และ Publish branch **ยังไม่ Merge**
4. กลับ main ซึ่งยังมีชื่อเดิม สร้าง `title-b` เปลี่ยนบรรทัดเดียวกันเป็น `Workshop title: GitHub Hands-On` Commit และ Publish branch
5. เปิด PR ของ `title-a` เข้า main และ Merge ก่อน
6. เปิด PR ของ `title-b` เข้า main ตอนนี้ทั้งสอง Branch แก้บรรทัดเดียวจากฐานเดิมและควรเกิด Conflict อย่า Pull main เข้า title-b ก่อนตรวจจุดนี้

## ลงมือทำ B · แก้ใน Desktop

1. ใน Desktop เลือก main → Fetch/Pull เพื่อรับผลจาก title-a ตรวจ Changes ว่าง
2. เลือก title-b → Current Branch → Choose a branch to merge into title-b → เลือก main → Merge main into title-b อ่านชื่อทิศทางให้ถูก
3. เมื่อโปรแกรมรายงาน Conflict ให้เปิด `notes/workshop-title.md` ในโปรแกรมแก้ไข อาจเห็นเครื่องหมาย `<<<<<<<`, `=======`, `>>>>>>>` คั่นสองชุดข้อความ ชื่อฝั่งขึ้นกับวิธี Merge อย่าเลือกจากคำว่า Current/Incoming อย่างเดียว
4. อ่านทั้งสองข้อเสนอ ตกลงข้อความสุดท้าย แล้วแทนทั้งช่วงที่ขัดกันด้วย:

```markdown
# Workshop Plan

Workshop title: GitHub Hands-On for Beginners
```

5. ลบ Conflict markers ทั้งหมด Save แล้วกลับ Desktop ตรวจว่าแก้ครบทุกไฟล์ จากนั้น Continue merge/Commit merge ตามที่โปรแกรมแสดง
6. Push title-b กลับเว็บ ตรวจ Files changed ของ PR อีกครั้ง ให้เพื่อนอ่านคำตัดสินแล้ว Merge เข้า main
7. กลับ main → Fetch/Pull และเปิดไฟล์ ตรวจว่ามีข้อความสุดท้ายบรรทัดเดียว

เส้นทางเว็บ: ใน PR title-b เลือก Resolve conflicts หากมีให้ใช้ แก้ข้อความและลบ markers → Mark as resolved → Commit merge แล้วตรวจ Diff ก่อน Merge PR ถ้าปุ่มนี้ใช้ไม่ได้ ให้ใช้ Desktop/เครื่องผู้สอนตามขั้นตอนข้างต้น

## ลงมือทำ C · Revert งานที่ Push แล้ว

1. บน main ที่ล่าสุดและไม่มีงานค้าง สร้าง `practice-revert`
2. เพิ่มบรรทัด `Temporary note: remove this after practice` ท้าย `notes/learning-log.md` Save และ Commit `docs: add temporary practice note` จากนั้น Publish branch
3. เลือก History คลิกขวา **Commit ที่เพิ่งเพิ่มข้อความทดลอง** → Revert Changes in Commit
4. ตรวจว่ามี Revert commit ใหม่ ข้อความทดลองหาย และ Commit เดิมยังอยู่ จากนั้น Push
5. เปิด History บนเว็บใน Branch `practice-revert` เก็บลิงก์ Commit เดิมและ Revert commit ไว้ในใบงาน ไม่ต้องเปิด PR เพราะผลสุทธิของ Branch นี้เท่ากับก่อนทดลอง
6. กลับ main ซึ่งไม่เคยได้รับข้อความทดลอง เก็บ Branch ไว้จนตรวจงานเสร็จ

ไม่ใช้ Reset, Rebase หรือ Force push ในกิจกรรมนี้ และอย่า Revert Merge commit แทน Commit ข้อความทดลอง ถ้าพบ Secret จริง การ Revert ไม่ลบ Secret จากประวัติ ต้องยกเลิก/เปลี่ยน Secret และให้ผู้ดูแลช่วยจัดการประวัติ

## Checkpoint

- [ ] มี Conflict จริงก่อนแก้และอธิบายสาเหตุได้
- [ ] main มีชื่อกิจกรรมสุดท้าย ไม่มี markers เหลือ
- [ ] Branch practice-revert มีทั้ง Commit ทดลองและ Revert commit แต่ข้อความทดลองหาย

## Mini Challenge

อธิบายให้เพื่อนฟังว่าทำไม Revert ที่สำเร็จยังมองเห็น Commit เก่า และเหตุใดเราไม่ต้อง Merge Branch ทดลองที่ไม่มีผลสุทธิ

## คำถามทบทวน

1. แก้คนละไฟล์ต้อง Conflict เสมอหรือไม่?
2. เหตุใดการเลือก Accept current ทั้งหมดโดยไม่อ่านอาจทำให้งานเพื่อนหาย?
3. ถ้า Commit มีรหัสผ่าน การ Revert เพียงอย่างเดียวเพียงพอหรือไม่?

[ก่อนหน้า](../06-pull-requests/README.md) · [ใบงาน 07](../../worksheets/07-conflicts-and-recovery.md) · [ถัดไป: บท 08](../08-issues-and-team-workflow/README.md)
