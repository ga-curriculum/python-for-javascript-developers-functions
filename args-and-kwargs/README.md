# ![Python Functions - Args and Kwargs](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to distinguish between "args" and "kwargs" and better know when to use them.

## Parameters & Arguments

Just like in JavaScript, **parameters** are the placeholders for passing input to a function.

```python
# a & b are parameters
def add(a, b):
  return a + b
```

Also like JavaScript, the values/expressions passed in to a function when calling it are known as **arguments**:

```python
num = 5

# num & 10 are arguments
add(num, 10)
```

However, unlike JavaScript, Python requires that the correct number of arguments be provided when calling a function. For example:

```python
def add(a, b):
  return a + b
  
add()
  
# Generates the following error:
# TypeError: add() missing 2 required positional arguments: 'a' and 'b'
```

## Accepting a varying number of arguments

In JavaScript, we were able to access "extra" arguments being passed in to a function by using the special `arguments`:

```javascript
// Using the arguments special variable
const sum() => {
  let total = 0;
  for (arg of arguments) total += arg;
  return total;
}

console.log( sum(1, 5, 10) );  // -> 16
```

Or preferably by using ES2015’s *rest parameters*:

```javascript
const sum = (...nums) => {
  return nums.reduce((sum, num) => sum + num, 0);
}

console.log( sum(1, 5, 10) );  // -> 16
```

### Python’s `*` Parameter Specifier (`args`)

Using the `*` ("star") specifier in a parameter list allows us to pass in a varying number of **positional** arguments into a function:

```python
def my_function(*args):
  print( type(args) )
  for arg in args:
    print(arg)

my_function(1, 2, 'SEI')
''' Output:
<class 'tuple'>
1
2
SEI
'''
```

The identifier used with `*`, i.e., `args`, can be anything, however **by convention, use `args`**.

Always use the `*args` parameter **after** any **required** positional parameters. For example:

```python
def dev_skills(dev_name, *args):
  dev = {'name': dev_name, 'skills': []}
  for skill in args:
    dev['skills'].append(skill)
  return dev

print(dev_skills('Alex', 'HTML', 'CSS', 'JavaScript', 'Python'))
# -> {'name': 'Alex', 'skills': ['HTML', 'CSS', 'JavaScript', 'Python']}
```

### Python’s `**` Parameter Specifier (`**kwargs`)

[https://s3-us-west-2.amazonaws.com/secure.notion-static.com/866439fb-27a8-4744-a435-5db6d1151e0d/zoom_0_(1).mp4](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/866439fb-27a8-4744-a435-5db6d1151e0d/zoom_0_(1).mp4)

If you’d like to be able to access a varying number of **keyword** arguments, use `**kwargs` at the **end of the parameter list**:

```python
def dev_skills(dev_name, **kwargs):
  dev = {'name': dev_name, 'skills': {}}
  # unpacking the tuples returned by the items function
  for skill, rating in kwargs.items():
    dev['skills'][skill] = rating
  return dev

print(dev_skills('Jackie', HTML=5, CSS=3, JavaScript=4, Python=2))
```

### Combining Required Positional, Optional Positional (`*args`) & Keyword (`**kwargs`) Arguments

You can define all three types of parameters in a function, but you have to do it in this order:

```python
def arg_demo(pos1, pos2, *args, **kwargs):
  print(f'Positional params: {pos1}, {pos2}')
  print('*args:')
  for arg in args:
    print(' ', arg)
  print('**kwargs:')
  for keyword, value in kwargs.items():
    print(f'  {keyword}: {value}')

arg_demo('A', 'B', 1, 2, 3, color='purple', shape='circle')

'''Output:
Positional params: A, B
*args:
  1
  2
  3
**kwargs:
  color: purple
  shape: circle
'''
```