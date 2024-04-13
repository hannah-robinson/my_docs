---
date created: 2024-05-13
last updated: 2024-05-13
programming language: python
library or framework: 
tags:
---
⬆ [[_Python_]]

```shell
xcode-select --install
brew install openssl readline sqlite3 xz zlib

brew update
brew install pyenv
echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
#OR (I did this next one)
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init --path)"' >> ~/.zshrc

# check versions of Python available for download
pyenv install -l  
pyenv install 3.12.3
pyenv versions

#install a global version
pyenv global 3.12.3

#install a local version
cd my_project
pyenv local 3.12.3
ls -a
cat .python-version

python -m venv .venv
source .venv/bin/activate
which python
```
(See: [[Create a Python virtual environment with venv]])
```python
# hello.py

import sys

print(f"Hello, I'm Python version: {sys.version} ")
```
## Configure project in VSCode
Tell VSCode to always activate venv when we enter this project, add a settings json to our project workspace

CMD + SHIFT + P (VSCode command palette)
Search: settings.json 
Choose: Open Workspace settings
It will create an empty settings.json file. Add this to it:
```json
{
  "python.terminal.activateEnvironment": true
}
```

Thank you so much for this video and the accompanying blog post! It is the clearest and most complete explanation I've found on how to set up a dev environment for Python projects.

---
🏷 Tags: 

🖇 Related links:

Videos: https://www.youtube.com/watch?v=31WU0Dhw4sk
^ This video is the most complete I've seen on dev environment setup for Python projects.

Linux version: https://www.youtube.com/watch?v=1Zgo8M9yUtM


