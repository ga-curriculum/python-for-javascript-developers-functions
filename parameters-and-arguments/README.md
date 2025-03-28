<h1>
  <span class="headline">Functions</span>
  <span class="subhead">Parameters and Arguments</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to declare a function with parameters and call a function using arguments.

## Parameters

In Python, **parameters** are variables that act as placeholders for values passed into a function.

```python
# text is a parameter
def print_banner(text):
    print("=======================")
    print(text)
    print("=======================")
```

The function above accepts one parameter, `text`. When the function is called, a value must be provided for this parameter.

## Arguments

An **argument** is the actual value you pass into a function when you call it. Just like in JavaScript, arguments are used to provide input to a function.

```python
# "hello, world" is an argument
print_banner("hello, world")
```

In this example, the value `"hello, world"` is passed to the function as the argument for `text`.

Unlike JavaScript, Python requires that you provide the correct number of arguments when calling a function. If you don’t, Python will raise an error.

```python
print_banner()

# Error:
# TypeError: print_banner() missing 1 required positional argument: 'text'
```

## Accepting a variable number of arguments

In JavaScript, we can use **rest parameters** to allow a function to accept any number of arguments:

```javascript
const sum = (...nums) => {
  total = 0;

  nums.forEach((num) => {
    total += num;
  });

  return total;
};

console.log(sum(1, 5, 10));
// prints: 16
```

### Python’s `*args` syntax

In Python, you can use the `*` (asterisk) before a parameter name to accept a variable number of **positional arguments**. This is commonly written as `*args`.

```python
def sum(*args):
    print(type(args))
    # prints: <class 'tuple'>

    total = 0
    for arg in args:
        total += arg

    return total

print(sum(1, 5, 10))
# prints: 16
```

The `args` parameter becomes a **tuple** that contains all the values passed to the function. The name `args` is a common convention, but you can technically use any name after the `*`.

### Mixing required and variable arguments

If your function has both required and variable arguments, the required ones must come **first**.

```python
def sum(greeting, *args):
    print(greeting)
    # prints: Hello, friend

    total = 0
    for arg in args:
        total += arg

    return total

print(sum("Hello, friend", 1, 5, 10))
# prints:
# Hello, friend
# 16
```

In this example, `"Hello, friend"` is passed as the required `greeting` argument, and the numbers are collected in `args`.
