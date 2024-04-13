---
date created: 2024-05-13
last updated: 2024-05-13
programming language: python
library or framework: 
tags:
---
⬆ [[_Python_]]

For Mac/Linux:
```shell
cd my_project
python3 -m venv env_name
source env_name/bin/activate
```
Once activated, your terminal prompt will change to indicate you are in the virtual environment. You can now install packages using pip and run your Python scripts as usual. Any changes you make, such as installing packages, will be confined to the virtual environment.

> [!NOTE] `venv` is only active in the terminal window you activated it in
> So if you activated it in the Terminal app before opening the project in VSCode and then you open VSCode's built-in CLI, you'll need to run `source env_name/bin/activate` again there before using the VSCode CLI to install any packages

See [[Configure project in VSCode]] for how to deal with this ^

When you've finished working in the virtual environment, you can deactivate it by running the following command:
```shell
deactivate
```

---
🏷 Tags: #🌱

🖇 Related links:
 [[Configure project in VSCode]] 

Videos: 
