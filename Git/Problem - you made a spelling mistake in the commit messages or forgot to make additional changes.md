---
date created: 2023-07-09
last updated: 2023-07-09
programme: git
tags: 
---
⬆ [[_Git_]]

Solution:
```bash
git commit --amend
```
- Can combine staged changes with the last commit instead of creating a new commit
- Can edit commit message of last commit
- You can add or remove changes from git staging and "amend" them into the last commit
The amended commit will actually be a brand new commit entirely (so be careful if this commit has already been pushed to remote)
```bash
git commit --amend -m "Count from 0 to 9"
```

---
🏷 Tags: #🌱

🖇 Related links:
