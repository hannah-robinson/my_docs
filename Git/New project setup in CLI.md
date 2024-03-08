---
last updated: 2024-03-09
programming language:
library or framework:
programme: git
platform: github
tags: 
---
⬆ [[_Git_]]

```bash
mkdir -p ~/repos/project-name
cd ~/repos/project-name
cp ~/repos/--templates/* .
cp ~/repos/--templates/.gitignore .gitignore
code ~/repos/project-name/.gitignore
code .
gh repo create <project-name> --private
# or:
# gh repo create <project-name> --public

git init
git add -A
git commit -am "Initial commit"
git remote add origin git@github.com:hannah-robinson/<project-name>.git
git push -u origin main
```

---
🏷 Tags: #🌱

🖇 Related links: [[GitHub]] 
