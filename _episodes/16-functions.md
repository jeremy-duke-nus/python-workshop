---
title: Building your own reusable code with functions
teaching: 30
exercises: 50
questions:
  - How do we create reusable codes in our program?
  - What are some best practices in writing reusable codes?
objectives:
  - Learn how to write your own function using best practices.
  - Understand the difference between local and global variables.
  - Create your first well-documented function.
keypoints:
  - Functions are the building block of programs.
  - Functions should be small and have minimal (or better, no) side effects.
  - Variables defined in a function are local and cannot be accessed outside of it.
---

# 🛠️ Functions — Your Code’s Superpowers

Alright team, it’s time to teach our code some manners. Yesterday, every time we wanted the program to do something, we had to give it step-by-step instructions right there in the moment. That’s like explaining how to make tea every time you want a cup. Exhausting.

Enter functions — the building blocks of programs.
A function is like a little magic box:

- You give it some input (ingredients),
- It does its thing (recipe),
- And hands you the output (final dish).

Today, we’ll:

- Learn to write our own functions (with good naming and clear purpose).
- Understand the difference between local variables (living only inside the function) and global variables (wandering around the whole program).
- Create your first well-documented function that’s small, tidy, and polite—minimal side effects only, thank you very much.
  By the end, your code will be more organized, easier to read, and you’ll wonder how you ever lived without functions.

# Writing your first function

Lets start with a simple task: Let's say we want to be able perform addition of two numbers. This is how the function will look like:

```python
def addition(x:int, y:int) -> int:
  return x + y

test_case = addition(1,3)
print (test_case)
# Output: 4
```

**Breaking it down**:

1. `def` – This is short for define. It tells Python: “Hey, I’m about to create a new function!”
2. `addition` – This is the function name. Use clear, descriptive names so future-you (and your teammates) don’t have to guess what it does.
3. `(x: int, y: int)` – These are the `parameters`. Parameters are like placeholders for the values your function will receive. Here, x and y are expected to be integers (int). The : int is a type hint—it tells humans and certain tools what kind of data should go here.
4. `-> int` – This is the return type hint. It suggests that this function will return an integer.
5. Function body – The indented line return x + y is where the magic happens.
6. `return` sends the result back to wherever the function was called.
7. Calling the function – `addition(1, 3)` is how we use the function. The numbers 1 and 3 are the arguments we’re passing in to replace x and y.
8. Storing the result – `test_case = addition(1, 3)` assigns the function’s output in a variable.

{:.challenge}

> ## Try it
>
> Using the above code as an example, write your first function to perform various mathematical operations such as `subtraction`, `multiplication` and `division`.

# Laziness is the goal of programming

What if you find yourself using the same values **most** of the time? Consider the example of the `addition` function we defined above. What if most of the time, we will be adding the same number to `x`? Here's where we can use _default values_. For example:

```python
def addition(x:int, y:int = 3) -> int:
  return x + y

test_case = addition(1)
print (test_case)
# Output: 4
```

We can supply default values to any parameter of choice. However, it is important to note that in Python, you **MUST** provide parameters without default values first before parameters with default values in your function definition. So this will not work:

```python
def addition(y:int = 3, x) -> int:
  return x + y

test_case = addition(1) # This will lead to an error
```

When we call functions with default arguments, we can simply provide values for parameter without default values if we are intending to use the default values.

# 🌍 Global vs 🏠 Local Variables

Yesterday, we had discussed what are variables in Python. In it, we said that variables are simply references to an address where the data sits on memory. This means that variables have homes. Where they live determines who can see them and how long they stick around. There are two types of variables: **Global** and **Local** variables.

## 1. Global Variables 🌍

Declared outside of any function, these variables can be accessed anywhere in the code (inside and outside functions).
Be careful: if too many parts of your code change the same global variable, things can get messy fast.

```python
message = "Hello from the outside!"  # Global variable

def greet():
    print(message)  # Can see the global variable

greet()
print(message)

#Output:
#Hello from the outside!
#Hello from the outside!
```

## 2. Local Variables 🏠

Declared inside a function. These variables exist only while that function is running and cannot be accessed outside the function—it’s like they vanish when the function finishes.

```python
def greet():
    name = "Alice"  # Local variable
    print(f"Hello, {name}!")

greet()
print(name)  # ❌ This will cause an NameError
```

{:.challenge}

> ## Try it
>
> Try running the code below to see what happens:
>
> ```python
> counter = 0
> def increment(increment:int) ->int:
>     print (counter + increment)
> increment()
> print (counter)
> ```

# We can (and should) combine many functions into a single function

In mathematics, we have composite functions (which are really just functions which taken the output of other functions as input). We can do similar things in Python. In fact, it is recommended that we break large, complex tasks into many smaller tasks because they make our codes much easier to understand, test and add new functionalities. We can also add conditional logic to orchestrate how our input is flowing through our function.

{:.challenge}

> ## Try it
>
> Using the small functions you wrote at the start of this section to perform `subtraction`, `multiplication` and `division`, write a calculator program that allows a user to provide the numbers alongside the mathematical operation. Use the following to help guide you:
>
> ```python
> # TODO: Create the smaller functions here:
> ____ addition(x:int, y:int) -> int:
>     return x + y
> ____ ________ -> int:
>     return x - y
> ____ ________ -> int:
>     return x * y
> ____ ________ -> float:
>     return x / y
>
> # TODO: Fill in the blanks, and update the function as needed.
>
> def calculator(x:int, y:int, operation: str):
>     if operation == "+":
>          return addition(x, y)
>     ____ operation == "-":
>          return substraction(x , y)
> # TODO: Add handling for * and / operations to this function
>
> print (calculator(1,3,'+')) # Output: 4
> print (calculator(1,3,'-')) # Output: 4
> ```

# The order in which you return makes a difference

# Conclusion
