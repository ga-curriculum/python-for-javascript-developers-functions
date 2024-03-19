# ![Python Functions - Calling Functions](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to call a function in Python.

## Calling Functions

In Python, calling functions is the same as it is in JavaScript:

```python
def add(a, b):
  return a + b
  
def sub(a, b):
  return a - b

def compute(a, b, op):
  return op(a, b)

print( compute(1, 2, add) )
```

Functions in Python can be passed to other functions - **callbacks** exist in Python!

Let’s learn more about Python’s **parameters** & **arguments**.
