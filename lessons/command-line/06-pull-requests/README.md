# CLI-06 · Pull Request และ Review ด้วย gh

## เป้าหมายและแนวคิด

ใช้ GitHub CLI เปิดและตรวจ PR หลัง Push งานด้วย Git ได้ Git ไม่มีคำสั่งสร้าง GitHub PR โดยตรง `git request-pull` ไม่ใช่คำสั่งเปิด GitHub PR ใช้ `gh pr` หรือเว็บไซต์แทน

เตรียมคู่ฝึก A/B รับคำเชิญ Collaborator ใน Repository ฝึกให้ครบ หากใช้ Private ผู้ตรวจต้องมีสิทธิ์เข้าถึงด้วย หากไม่ให้สิทธิ์ Push ใช้ [Fork workflow](../../../appendix/fork-workflow.md) และเปิด PR จาก Fork บนเว็บตามคู่มือ

## ลงมือทำ A · ผู้เขียนเปิด PR

กลับสำเนาหลัก `add-project-page` ยังอยู่จาก CLI-04 ส่วน main ได้รับงาน Sync จาก CLI-05 แล้ว ให้ Merge main ล่าสุด **เข้า Branch งาน** ก่อนเปิด PR:

```bash
git switch main
git pull --ff-only
git switch add-project-page
git merge --no-edit main
git diff main...HEAD
git push
```

หากการ Merge เกิด Conflict ให้อ่านและจัดการตาม CLI-07 ก่อนทำต่อ คำสั่ง `diff main...HEAD` เปรียบเทียบฐานร่วมกับปลาย Branch งาน เหมาะกับดูสิ่งที่จะเสนอใน PR

```bash
gh pr create --base main --head add-project-page --title "Add first project page" --body "Adds projects/first-project.md and a link from README. Checked the Markdown preview and navigation."
gh pr view --json number,url,state,baseRefName,headRefName
gh pr diff
```

จดเลข PR จริงที่ได้ ไม่สมมติว่าเป็น #1 แทน `PR_NUMBER` ในตัวอย่างถัดไปก่อนรัน และใช้เลขเดิมในการ Review/Merge

## ลงมือทำ B · ผู้ตรวจอ่านงาน

B เปิด Terminal ใน Clone ของ Repository A และ Login เป็นบัญชี B ตรวจ Remote และบัญชีก่อนทำงาน:

```bash
git remote -v
gh auth status --hostname github.com
gh pr view PR_NUMBER
gh pr diff PR_NUMBER
gh pr checkout PR_NUMBER
```

อ่านไฟล์ใน Branch ที่ Checkout และลองลิงก์ใน editor/เว็บ ถ้า B มีงานค้างต้องเก็บก่อน Checkout อย่าใช้ Force ข้าม ให้ข้อเสนอแนะที่ระบุจุดและเหตุผล:

```bash
gh pr review PR_NUMBER --comment --body "Please make the Expected Result measurable so readers can verify the README link."
```

A แก้ Expected Result ในหน้าโปรเจกต์บน Branch เดิมให้ระบุผลชัดขึ้น จากนั้น:

```bash
git add projects/first-project.md
git diff --staged
git commit -m "docs: clarify expected project result"
git push
```

PR เดิมจะอัปเดต ไม่ต้องสร้าง PR ใหม่ B อ่าน Diff รอบใหม่ เมื่อผ่านเกณฑ์จึง:

```bash
gh pr diff PR_NUMBER
gh pr review PR_NUMBER --approve --body "The expected result and README link are clear."
```

ผู้เขียน PR อนุมัติ PR ของตนเองไม่ได้ ต้องใช้บัญชีอีกคน ส่วน Comment ธรรมดาไม่ได้เท่ากับ Approve

## ลงมือทำ C · เจ้าของ Merge และรับงาน

เจ้าของตรวจเป้าหมาย สิทธิ์และสถานะ Review ก่อน Merge:

```bash
gh pr view PR_NUMBER --json state,baseRefName,headRefName,reviewDecision,mergeable
gh pr merge PR_NUMBER --merge
gh pr view PR_NUMBER --json state,mergedAt,url
git switch main
git pull --ff-only
git status --short --branch
```

`--merge` ขอใช้ Merge commit ใช้ใน Repository ฝึกที่อนุญาตวิธีนี้ หากทีมอนุญาตเฉพาะ Squash/Rebase หรือมี Required checks ให้ทำตามนโยบาย Repository ไม่ใช้ `--admin` ข้ามข้อกำหนด หากเข้า Merge queue ให้ตรวจจน state เป็น MERGED ก่อนอ้างว่างานเสร็จ

ไม่มี gh: Push ด้วย Git แล้วใช้เว็บเปิด PR, Review และ Merge ตาม [บท Desktop/เว็บ 06](../../06-pull-requests/README.md) กลับมารัน switch/pull ด้วย Git เหมือนเดิม

## Demo และ Checkpoint

ผู้สอนใช้สองบัญชีตามบทบาท แสดงว่า PR อัปเดตหลัง Push เพิ่มโดยไม่เปลี่ยนเลข PR

- [ ] Base เป็น main, Head เป็น add-project-page และมี Diff ที่ตั้งใจ
- [ ] มี Review จากเพื่อนและการปรับตาม Comment
- [ ] PR เป็น MERGED และ main บนเครื่องมีหน้าโปรเจกต์

## Mini Challenge และทบทวน

สลับบทบาทให้ B เสนอแก้ Learning log ผ่าน Branch ใหม่ A เป็นผู้ตรวจ อธิบายว่า `gh pr checkout` กับ `git pull` ทำหน้าที่ต่างกันอย่างไร

[ก่อนหน้า](../05-sync-and-remotes/README.md) · [ใบงาน](../../../worksheets/command-line/06-pull-requests.md) · [ถัดไป](../07-conflicts-and-recovery/README.md)
