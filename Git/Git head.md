---
date created: 2024-01-21
last updated: 2024-01-21
programming language: 
library or framework: 
programme: git
platform: 
tags:
---
⬆ [[_Git_]]

![[Pasted image 20240121133205.png]]
*Image source: https://www.udemy.com/course/git-and-github-bootcamp/learn/lecture/24619686#overview [[The Git and Github Bootcamp]]*

Head not necessarily the most recent commit across all branches; it is the pointer to which branch you are currently on. Head moves each time you checkout a different branch. You can think of it like a book mark.
```bash
git switch ibd
cat .git/HEAD
> ref: refs/heads/ibd
# the contents of a file in the `heads` directory is just a commit hash
```

---
🏷 Tags: #🌱

🖇 Related links:
