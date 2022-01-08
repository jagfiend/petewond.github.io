---
layout: post
title: "Learning Python 1 - Functions"
date: 2022-01-07 15:40:00 +0000
published: true
---

I started teaching myself Python towards the end of 2021. Initially I watched some YouTube videos and would recommend the following videos / channels:

+ [freeCodeCamp](https://www.youtube.com/c/mCodingWithJamesMurphy/featured) - I watched the 4hr Django beginners course and the 10hr Python Backend Dev course (at x1.5 speed!).
+ [mCoding](https://www.youtube.com/c/mCodingWithJamesMurphy/featured) - Good for understanding general, advanced and odd bits of the language.
+ [Python Programmer](https://www.youtube.com/channel/UC68KSmHePPePCjW4v57VPQg) - Good for understanding the fundamentals, more data science orientated.

I decided to do more active learning and learn the basics of the language outside a web development context (more on this in the future) so signed up for the Python Programmer [Python for Absolute Beginners - Python Beginner to Pro 2021](https://www.udemy.com/course/the-complete-python-programmer-bootcamp/) course.

From this course I have gained an overview of the fundamentals such as variable assignment, control flow and got passed the weird feeling of not typing `{}` to define blocks and ending lines with semicolons (something I do in JavaScript as well as PHP). I played around with functions, inevitably with some Fibonacci variations:

```python
def basic_function():
    '''Basic function definition with a docstring, this will appear in the autocompletion description.'''
    print(f"something something darkside")

basic_function()
# Running this script in the VS Code terminal prints somthing something darkside

def type_hint_example(name: str) -> str:
    '''Function with type hinting, here we are telling the user that the name arg is expecting a str and the function returns a string.
    Python doesn't actually enforce the type though which makes me a bit sad. 
    Type hinting simple functions also makes docstrings redundant #irony'''
    return f"Hello {name}"

x = type_hint_example('Pete')
y = type_hint_example(123)
print(f"x: {x}, y: {y}")
# Running this script in the VS Code terminal prints x: Pete, y: 123

def fib(n):
    '''Calculates and returns the nth fibonacci number using a loop.'''
    a = 0
    b = 1
    for i in range(n):
        a,b = b,a+b
    return a

print(fib(20))
# Running this script in the VS Code terminal prints 6765

def fib_recursive(n):
    '''Calculates and returns the nth fibonacci number using recursion.'''
    if n == 0:
        return 0
    elif n == 1:
        return 1
    
    return fib_recursive(n - 1) + fib_recursive(n - 2) 

print(fib_recursive(6))
print(fib_recursive(7))
print(fib_recursive(8))
print(fib_recursive(50))
# Running this script in the VS Code terminal prints 8 13 21 and hangs as recursion can be a memory hog.

def fib_recursive_memoized(n, memo = {}):
    '''Calculates and returns the nth fibonacci number using memoization to improve performance.'''
    if n in memo:
        return memo[n]
    elif n == 0:
        return 0
    elif n == 1:
        return 1

    memo[n] = fib_recursive_memoized(n - 1, memo) + fib_recursive_memoized(n - 2, memo)

    return memo[n]

print(fib_recursive(6))
print(fib_recursive(7))
print(fib_recursive(8))
print(fib_recursive(50))
# Running this script in the VS Code terminal prints 8, 13, 21 and 12586269025 instantly, hoozah.
```

Note on memoization: I found a more 'Pythonic' / advanced way to do this is with a [decorator helper function](https://python-course.eu/advanced-python/memoization-decorators.php) helper function. I may come back this!
