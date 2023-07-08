---
date created: 2023-07-07
last updated: 2023-07-07
programming language:
library or framework:
programme: git
platform:
tags: 
alias: Create a remote branch for your local branch
---
⬆ [[_Git_]]

>[!quote] Actually, Git does _not_ allow creating a (new, isolated) branch on a remote repository. Instead, you can **push** an **existing local** branch and thereby publish it on a remote repository.

Source: https://www.git-tower.com/learn/git/faq/git-create-remote-branch/

```bash
git push -u origin <branch-name>
```

>[!info] The `-u` option establishes a tracking relationship between the existing local and the new remote branch. This means for any future "push" and "pull" operations you can just use `git push` or `git pull` without any further options.

---
🏷 Tags: #🌱

🖇 Related links:
[[_Git_]]