# CLI-04 · Branch และ Merge

## เป้าหมายและแนวคิด

แยกงานใหม่ ตรวจ Branch และทดลอง Local merge ได้ `git switch -c NAME` สร้างและย้ายไป Branch ใหม่ ส่วน `git merge SOURCE` รวม SOURCE **เข้า Branch ที่กำลังอยู่** จึงต้องตรวจปลายทางก่อน Merge

## ลงมือทำ A · เพิ่มหน้าโปรเจกต์

```bash
git status --short
git switch main
git pull --ff-only
git switch -c add-project-page
mkdir -p projects
```

หาก status มีงานค้างให้ Commit งานนั้นก่อน เริ่มไฟล์ใหม่ `projects/first-project.md` ด้วย editor:

```markdown
# My First Project Idea

## Problem
ต้องการรวบรวมผลงานที่อ่านได้ง่าย

## Proposed Solution
จัดหน้าแนะนำผลงานใน GitHub

## Expected Result
เปิดหน้าโปรเจกต์จาก README ได้
```

เพิ่ม `[First project](projects/first-project.md)` ใน README แล้ว Save ตรวจทั้งสองไฟล์:

```bash
git status --short
git diff
git add README.md projects/first-project.md
git diff --staged
git commit -m "docs: add first project page"
git switch main
git ls-tree -r --name-only HEAD
git switch add-project-page
git ls-tree -r --name-only HEAD
git log --oneline --graph --decorate --all -10
git push -u origin add-project-page
```

main ยังไม่มีหน้าใหม่ Branch งานมีหน้าใหม่ `-u` ผูก Local branch กับ Remote-tracking branch เพื่อใช้ Push/Pull ครั้งต่อไปได้โดยไม่ใส่ชื่อซ้ำ เก็บ `add-project-page` ไว้เปิด PR ใน CLI-06 **ยังไม่ Merge เข้า main**

## ลงมือทำ B · ทดลอง Local merge บน Branch แยก

การทดลองนี้ช่วยแยก Git merge ออกจาก GitHub Pull Request ไม่แตะ main

```bash
git switch -c merge-practice main
git branch --show-current
git merge --ff-only add-project-page
git log --oneline --graph --decorate -6
git switch add-project-page
git branch -d merge-practice
```

เพราะ main ยังไม่มีงานใหม่ จึง Fast-forward merge ได้ โดยเลื่อนปลาย Branch ไม่สร้าง Merge commit ใหม่ หลังสลับกลับ add-project-page จึงลบชื่อ Branch ฝึกที่มีงานอยู่ใน HEAD ปัจจุบันแล้วด้วย `branch -d` หาก Git เตือนว่ายังไม่รวมงาน ให้ตรวจ Graph และเก็บ Branch ไว้ก่อน ไม่ใช้ `-D` บังคับลบเพื่อให้ผ่านบทเรียน

## Demo และ Checkpoint

ผู้สอนเปรียบเทียบ `main`, `add-project-page` และ `merge-practice` ใน Graph หากลบ Branch ฝึกแล้วให้ย้อนดูขั้นก่อนลบ

- [ ] Branch งาน Publish แล้ว main ยังไม่มีหน้าใหม่
- [ ] อธิบายทิศทาง Merge และ Fast-forward ได้
- [ ] ไม่มีงานค้างก่อนสลับ Branch

## Mini Challenge และทบทวน

เพิ่มหัวข้อ Next Steps บน `add-project-page` Commit และ Push แล้วอ่าน `git branch -vv` ว่า Branch ใดติดตาม origin/Branch ใด

[ก่อนหน้า](../03-staging-and-commits/README.md) · [ใบงาน](../../../worksheets/command-line/04-branches-and-merges.md) · [ถัดไป](../05-sync-and-remotes/README.md)
