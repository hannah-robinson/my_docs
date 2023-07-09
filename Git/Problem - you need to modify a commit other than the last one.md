---
date created: 2023-07-09
last updated: 2023-07-09
programme: git
tags: 
---
⬆ [[_Git_]]

Problem: you need to modify a commit other than the last one. You accidentally added a cat.txt file to a commit, 2 commits ago (i.e. in your second-to-last commit)

Solution:

```bash
git rebase HEAD~2 -i
# in editor that opens change `pick` to `edit` for the relevant commit and close it
git rm --cached cat.txt
git commit --amend
git rebase --continue

```
---
🏷 Tags: #🌱

🖇 Related links:
