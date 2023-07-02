---
date created: 2023-07-02
last updated: 2023-07-02
programme: git
tags: 
---
⬆ [[_Git_]]

Scenario: you have a feature branch called `ibd` that you want to rebase onto `main`.
Checkout `ibd` and then use the command below.  The hash should be the hash of the commit after which the two branches diverged.
 ```
git rebase --onto main 77d0ca65b3e430fb338d90620dc6184444835840
 ```
Assuming you are using VS Code with GitLens and Git Graph plugins, hit ctrl, shift, G to open source control in left-hand panel. Resolve any conflicts in files that are listed in the panel, save the files and click the + button beside them to add them to staging. Then:
```
git rebase --continue
```
If  you clicked the continue button in VS Code's left-hand panel GUI instead, the terminal won't initially know the rebase has been completed. Just do a `git status` and the terminal will come out of rebase mode and then you can continue with your next operation.

---
🏷 Tags: #🌲

🖇 Related links:
[[How we fixed the my_docs supposedly missing files issue]]
