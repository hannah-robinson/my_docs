---
date created: 2023-07-02
last updated: 2023-07-02
programme: git
tags: 
---
⬆ [[_Git_]]
We used the terminal and VS Code with 2 plugins: GitLens by GitKraken (extension id: eamodio.gitlens) and Git Graph (extension id: mhutchie.git-graph).

In VS Code, you can get to the source control panel with ctrl, shift, G. It'll open in the left-hand panel. You'll see GitLens there.

There will also be a button to open Git Graph. It's the last one in the row.

![[Pasted image 20230702164743.png]]
Using Git Graph you can easily see at exactly which commit main and origin/main diverged. The hash in the cli commands below, is the hash of the commit at that nexus.

cli commands used were:
 ```bash
 git diff --name-only main origin/main 
 # look at code differences
 
 git branch -c ibd 
 # while on main, make a copy of (local) main called ibd, ibd now has all the new commits origin/main doesn't
 
 git reset --hard origin/main
 # while on main, reset local head to same commit as remote head
 
 git checkout ibd
 git branch -c ibc2
 # while on ibd, make a copy of ibd called ibc2 (as a backup)
 
 git rebase --onto main 77d0ca65b3e430fb338d90620dc6184444835840
 # while on ibd, rebase ibd onto main
 
 git status
 git checkout main
 git merge ibd
 # while on main, (fast forward) merge ibd into main
 
 git push
 ```

---
🏷 Tags: #🌲 

🖇 Related links:
[[Create a new branch without checking it out]]
[[Reset local branch to the same head as remote branch]]
[[Git rebase onto another branch at a specific commit]]
