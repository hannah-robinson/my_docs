---
date created: 2024-05-13
last updated: 2024-05-13
programming language: python
library or framework: 
tags:
---
⬆ [[_Python_]]

In a function definition, you can use `: int` to specify that an integer is the expected type of argument and the arrow (`->`) to specify the return type of the function. This is known as type hinting. 

```python
def add_numbers(x: int, y: int) -> int:     
  return x + y
```

```python
def api_call(url: str, *, key: str) -> str:
  return '/'.join([url, key])
```
The type hints are optional and do not enforce type checking at runtime. However, they can be useful for code readability and documentation, and some tools like linters and IDEs can use them to provide feedback and warnings during development. 

Python is a dynamically-typed language, so type hints do not change the nature of the language or enforce strict type checking. But, you can use tools such as [**mypy**](http://mypy-lang.org/) to perform static type checking on your code and identify potential type-related issues. 

---
🏷 Tags: #🌱

🖇 Related links:

Videos: 