# CLI · ปัญหาที่พบบ่อย

| อาการ | ตรวจอะไร | แนวทาง |
|---|---|---|
| git/gh: command not found | Version และ Terminal ที่เปิดหลังติดตั้ง | ติดตั้งเครื่องมือที่ขาด เปิด Terminal ใหม่ |
| not a git repository | `pwd` และโฟลเดอร์ที่ทำงาน | cd เข้าโฟลเดอร์ที่ init/clone แล้ว ไม่ init ในตำแหน่งที่ผิดเพื่อให้ข้อความหาย |
| Author identity unknown | `git config --get user.name` และ user.email | ตั้ง Identity ให้ถูกก่อน Commit |
| remote origin already exists | `git remote -v` | ถ้าถูกแล้วไม่ต้อง Add ซ้ำ ถ้าผิดให้ตรวจ URL แล้วใช้ `git remote set-url origin URL` |
| Repository not found | URL, บัญชี และสิทธิ์ Private | ตรวจ Owner/name และสิทธิ์ บางครั้ง GitHub ไม่เปิดเผยว่ามี Private repo อยู่ |
| Authentication failed | `gh auth status` หรือ Credential helper ที่เลือก | เข้าสู่ระบบด้วยวิธีที่ถูก ไม่ใส่ Password/Token ลงใน URL |
| Nothing to commit | status และการ Save | งานอาจยังไม่ Save, ถูก Ignore หรือ Commit ไปแล้ว |
| git diff ว่างแต่มี ?? | ไฟล์ Untracked | อ่านไฟล์ก่อน Add แล้วใช้ diff --staged |
| ไฟล์มี AM | diff และ diff --staged | Save หลัง Add ทำให้สองสถานะต่างกัน ต้อง Add ใหม่เพื่อเลือกเนื้อหาล่าสุด |
| ไม่มี Upstream | `git branch -vv` | ตรวจ Branch แล้ว `git push -u origin BRANCH_NAME` |
| Non-fast-forward rejection | Fetch แล้วอ่าน Graph | เก็บงาน local, Fetch และ Merge อย่างมีเหตุผล ไม่ Force push |
| pull --ff-only หยุด | Graph ของ Local/Remote | แยกว่าประวัติ Diverged หรือ Branch ผิด แล้วเลือก Merge ตาม CLI-05 |
| สลับ Branch ไม่ได้เพราะงานค้าง | status และ Diff | Commit งานที่ต้องเก็บบน Branch ที่ถูกก่อนสลับ |
| Merge มี Conflict | status และ `git diff --name-only --diff-filter=U` | แก้เนื้อหา, Add, Commit หรือ merge --abort ขณะ Merge ค้าง |
| gh review Approve ไม่ได้ | บัญชีและผู้เขียน PR | ให้ผู้เรียนอีกคน Review พร้อมตรวจสิทธิ์ |
| gh merge ไม่สำเร็จ | Review, checks, วิธี Merge ที่อนุญาต | ปฏิบัติตามนโยบาย ไม่ใช้ --admin ข้าม |
| gh issue/pr ใช้กับ Repo ผิด | `git remote -v`, `gh repo view` | cd เข้า Clone ที่ถูก หรือใส่ `--repo OWNER/REPO` ให้ชัดเมื่อคำสั่งรองรับ |
| จอค้างที่ END หรือ : | Pager ของ Git | กด q เพื่อออก ใช้ลูกศรเลื่อนอ่านได้ |
| ต้องการยกเลิกคำสั่งที่กำลังรอ | อ่านว่าเป็น editor, pager หรือ Login | q ใช้กับ Pager; Ctrl+C ยกเลิกคำสั่งที่กำลังรอ อย่าสุ่มปิด Terminal ระหว่าง Merge โดยไม่ตรวจสถานะ |

หลังคำสั่งเขียนงานทุกครั้งอ่านผลก่อนทำต่อ อย่าส่ง `gh auth token`, Private key, URL ที่ฝัง Credential หรือไฟล์ Credential เพื่อขอความช่วยเหลือ ส่งเฉพาะข้อความผิดพลาดที่ลบข้อมูลลับแล้ว

[สารบัญ CLI](README.md) · [อ้างอิง](references.md)
