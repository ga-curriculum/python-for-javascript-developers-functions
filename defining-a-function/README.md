# ![Python Functions - Defining a Function](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to define a function in Python.

## Defining Functions in Python

Here's how we define a basic function in Python:

```python
def fahr_to_kelvin(temp):
	return ((temp - 32) * (5/9)) + 273.15
```

As you can see:

- The first line starts with the `def` keyword. This defines a function.
- The next word is the name (identifier) of the function.
- Following that is a parameter list inside parentheses.
- The first line ends with a colon.
- The first line is followed by an indented code block that we have become familiar with.
- Python functions, like JavaScript, optionally return a value using a `return` statement.

## A Minimal Function in Python

In JavaScript, we often would create an "empty" function temporarily.

In a Python repl, let’s "stub up" a function Python:

```python
def first_function():
  pass
```

The `pass` statement is simply a "do nothing" statement and is useful here to create a function that has at least one statement in its block, which is a requirement.

- What does a JS function return by default if it doesn’t include a return statement?
    `undefined`
    

Let's see what a Python function returns by default:

```python
def first_function():
  pass

# Assign value returned by default
result = first_function()
print(result)
```

## Key Differences Between Python & JS Functions

Besides the obvious syntactical differences, here are a few other things to be aware of:

### Function expressions do not exist in Python

Functions in Python are defined using the `def` keyword. However, unlike in JavaScript, you cannot define a function in Python by assigning it to a variable:

```python
# This will not work
my_function = def my_function():
  pass
```

### Python has a different sort of anonymous/inline function

Python does have a the concept of anonymous and/or inline functions - called `lambda` functions.

`lambda` functions are very much like *Arrow Functions* in JavaScript:

- They implicitly return a single expression's result.
- They can be assigned to a variable.

However, they cannot have any code block - only a single expression that has its result implicitly returned.

For example:

```javascript
const nums = [1, 3, 2, 6, 5];
let odds = nums.filter(num => num % 2);
```

```python
nums = [1, 3, 2, 6, 5]
odds = list( filter(lambda num: num % 2, nums) )
```

Lambda functions are nifty when using Python functions such as `map()` - just like how arrow functions are nifty when using array iterator methods.

Check out [**this writeup**](https://realpython.com/python-lambda/) and the [**Python docs**](https://docs.python.org/3/reference/expressions.html#lambda) for more details.

[How to Use Python Lambda Functions - Real Python](https://realpython.com/python-lambda/)

### Python does not “hoist” functions

The last key difference between Python and JavaScript functions is that you cannot invoke a Python function before the code that defines it:

```python
# Not allowed until after the code below
add(5, 10)

def add(a, b):
  return a + b
```
