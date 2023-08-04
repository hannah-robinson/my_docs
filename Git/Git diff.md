---
date created: 2023-08-03
last updated: 2023-08-03
programming language:
library or framework:
programme: git
platform:
tags: 
---
⬆ [[_Git_]]

**Compare staging and working directory**
```bash
git diff
```

**See changes since HEAD (usually last commit) including both staged and unstaged changes**
```bash
git diff HEAD
```

**See differences between staged files and last commit**
```bash
git diff --staged
```
or
```bash
git diff --cached
```

**Compare between two branches**
```bash
git diff branch1..branch2
```
or
```bash
git diff branch1 branch2
```

**Compare between two commits**
```bash
git diff commit1..commit2
```
or
```bash
git diff commit1 commit2
```

**Compare versions of one file only**
```bash
git diff branch1..branch2 file.txt
```

```bash
git diff branch1 branch2 file.txt
```


🏷 Tags: #🌱

🖇 Related links:
