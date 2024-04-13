---
date created: 2024-05-13
last updated: 2024-05-13
programming language: python
library or framework: 
tags:
---
⬆ [[_Python_]]

```python
from dotenv import load_dotenv
import os

load_dotenv('.env')

username: str = os.getenv('USERNAME')
password: str = os.getenv('PASSWORD')
api_key: str = os.getenv('API_KEY')

print(username, password)

def api_call(url: str, *, key: str) -> str:
  return '/'.join([url, key])

result: str = api_call('helloworld', key=api_key)
print(result)
```

  Now in the root directory of your project you can create a file called `.env` to add the secrets to. Remember to add`.env` to your `.gitignore` file.
```python
API_KEY=j234hajs3rrhsfd
USERNAME=Juanita874
PASSWORD=password
```

For anyone else using your repo you can add a `template.env` file so they know to add those secrets there.
```python
API_KEY=
USERNAME=
PASSWORD=
```

---
🏷 Tags: #🌱

🖇 Related links:

Videos: 
