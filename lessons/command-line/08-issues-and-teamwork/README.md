# CLI-08 · Issues และ Workflow ของทีม

## เป้าหมายและแนวคิด

สร้างงานที่ตรวจรับได้ ทำ Branch/Commit/PR และยืนยันปิด Issue ด้วยคำสั่งได้ Issue ระบุสิ่งที่ต้องทำ ส่วน PR แสดงสิ่งที่เปลี่ยน `Closes #N` ใน PR description ปิด Issue เมื่อ Merge เข้า default branch ในชุดนี้คือ main

## ลงมือทำ A · เปิด Issue

```bash
git switch main
git pull --ff-only
git status --short
gh issue create --title "Add navigation back to README" --body "Add a Back to home link to projects/first-project.md. Acceptance criteria: the link opens README and existing content remains intact."
gh issue list --state open
```

จดเลข Issue ที่ได้จริง แทน `ISSUE_NUMBER` ในคำสั่งต่อไปก่อนรัน เลข PR/Issue อาจไม่เรียงตรงกับบทเรียนและไม่จำเป็นต้องเป็น #1

## ลงมือทำ B · ทำงานตาม Issue

```bash
git switch -c issue-ISSUE_NUMBER-add-navigation
```

ใน `projects/first-project.md` เพิ่ม `[Back to home](../README.md)` ด้วย editor แล้ว Save ตรวจลิงก์ใน Markdown Preview และบน Branch ที่ Push จริง:

```bash
git diff
git add projects/first-project.md
git diff --staged
git commit -m "docs: add navigation back to README"
git push -u origin HEAD
gh pr create --base main --title "Add navigation back to README" --body "Adds a Back to home link in projects/first-project.md. Checked that the link opens README and existing content remains intact. Closes #ISSUE_NUMBER"
```

`origin HEAD` ส่ง Branch ที่กำลัง Checkout ไปชื่อเดียวกันบน origin ในบริบท Branch ปกติของกิจกรรมนี้ ตรวจชื่อด้วย `git branch --show-current` ก่อน Push อย่าใช้ขณะ Detached HEAD

## ลงมือทำ C · Review, Merge และตรวจผล

ให้คู่ฝึกใช้บัญชีของตนเองอ่าน PR และ Approve ตาม CLI-06 โดยแทน `PR_NUMBER` ด้วยเลข PR ใหม่ จากนั้นเจ้าของ:

```bash
gh pr view PR_NUMBER --json state,baseRefName,headRefName,reviewDecision,mergeable
gh pr merge PR_NUMBER --merge
gh pr view PR_NUMBER --json state,mergedAt,url
gh issue view ISSUE_NUMBER --json number,state,url,closedAt
git switch main
git pull --ff-only
git status --short --branch
```

PR ต้องเป็น MERGED และ Issue เป็น CLOSED หากยังไม่ปิด ให้ตรวจ Keyword ใน description, เลข Issue, Repository และ default branch ก่อนสั่งปิดเอง ไม่ใช้การปิดเองแทนหลักฐานว่าการเชื่อมทำงานได้

ไม่มี gh: ใช้เว็บสร้าง Issue/PR/Review และตรวจสถานะตาม [บท 08](../../08-issues-and-team-workflow/README.md) แต่ใช้คำสั่ง Git ในชุดนี้เพื่อแก้ ส่ง และรับไฟล์

## การจบงานและเริ่มงานถัดไป

หลัง Pull main และตรวจว่ามีงานที่ Merge แล้ว สามารถลบ Branch ที่ไม่ใช้อยู่ด้วย `git branch -d BRANCH_NAME` และลบ Remote branch จากหน้า PR หรือ `git push origin --delete BRANCH_NAME` เมื่อทีมตกลงว่าไม่ใช้งานแล้ว ถ้าใช้ Squash/Rebase merge แล้ว `-d` เตือนว่าไม่ Merge ให้ตรวจผลและเก็บไว้ก่อน ไม่บังคับลบเพื่อความเรียบร้อย

## Demo และ Checkpoint

ผู้สอนให้ผู้เรียนเปิด Issue จาก Terminal แล้วอธิบายว่าเกณฑ์ตรวจรับแต่ละข้อผ่านจากไฟล์ใด

- [ ] Issue มีเกณฑ์ตรวจรับจริงและ PR อ้างเลขถูก
- [ ] มี Review จากคนอื่นและ PR เป็น MERGED
- [ ] Issue ปิดหลัง Merge เข้า main และ Local main อัปเดตแล้ว
- [ ] อธิบายสิ่งที่แต่ละคำสั่งเปลี่ยน ไม่ใช่เพียง Copy คำสั่ง

## Mini Challenge · ชิ้นงานปลายทาง

เลือกปรับปรุงอีกหนึ่งเรื่อง เปิด Issue และทำ Workflow ด้วยตนเอง ส่ง Repository, Issue, PR และ Commit พร้อมหลักฐาน Staging, Sync และ Recovery ตาม [ใบงาน CLI](../../../worksheets/command-line/README.md) ใช้ [ใบงานชิ้นงานปลายทางเดิม](../../../worksheets/final-project.md) ประกอบ โดยระบุเส้นทางว่า Command Line

[ก่อนหน้า](../07-conflicts-and-recovery/README.md) · [ใบงาน](../../../worksheets/command-line/08-issues-and-teamwork.md) · [สารบัญ](../README.md)
