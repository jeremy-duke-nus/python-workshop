---
title: Managing user and code failures
teaching: 30
exercises: 20
questions:
  - How are errors handled in Python?
  - What are some common coding practices to handle errors in programming?
objectives:
  - Know what are the different types of errors in Python.
  - Be able to write codes to manage errors using custom logic.
keypoints:
  - Functions should never fail silently.
  - Errors should be explicitly handled.
---

# ⚠️ When Python Complains (a.k.a. Error Handling)

If functions are polite, predictable helpers, then Python errors are the noisy pasar malam sellers. They don’t whisper—they shout:

```python
NameError: name 'varible' is not defined
```

Python isn’t yelling for fun—it’s telling you exactly what’s wrong, so you can fix it (or if you so desire, your codes can handle it). Errors happen when:

- You ask for something that doesn’t exist (`NameError`).
- You try to do something impossible (`ZeroDivisionError`).
- You give the wrong kind of data (`TypeError`).

Just like we prepare for rain with an umbrella, we can prepare our programs for errors using error handling. With try and except, we can tell Python:

> “If something goes wrong, don’t crash—here’s what to do instead.”

By the end of this section, you’ll:

1. Recognize common errors.
2. Write code that handles them gracefully.
3. Make your programs more reliable and user-friendly.
4. And yes—this is when we’ll let Python complain… but we will be responsible MPs and respond quickly to these complains to make sure they do not cause our programs to do things it should not do.

# Common Errors and their causes

Before we delve into how to handle errors, lets start with a list of common errors you will encounter and why

| **Error Type**                        | **Root Cause**                                                                                                 |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `SyntaxError`                         | The code violates Python’s grammar rules (e.g., missing a colon, unbalanced brackets).                         |
| `NameError`                           | You tried to use a variable or function name that hasn’t been defined yet.                                     |
| `TypeError`                           | An operation or function is applied to an object of an inappropriate type (e.g., adding a string to a number). |
| `ValueError`                          | A function receives the correct type but an invalid value (e.g., `int("hello")`).                              |
| `ZeroDivisionError`                   | You tried to divide a number by zero.                                                                          |
| `IndexError`                          | You tried to access a list or tuple element that doesn’t exist (out of range).                                 |
| `KeyError`                            | You tried to access a dictionary key that doesn’t exist.                                                       |
| `AttributeError`                      | You tried to access an attribute or method that an object doesn’t have.                                        |
| `ImportError` / `ModuleNotFoundError` | Python can’t find the module or object you’re trying to import.                                                |
| `FileNotFoundError`                   | You tried to tell Python to access a non-existent file                                                         |

While these are the most common errors, there are in actual fact a lot more standard errors, as well as custom errors that are library specific (a bit like us Singaporeans - Python too has a specific way to complain about any and everything). Now that we have been introduced to what the common complains are, what can we do about them?

# Error handling in Python

By default, when Python runs into an error, it will simply throw its arms up and say

> “I give up, fix this first!” and then stop the whole program right there.
> That’s fine for you as the programmer—because it tells you exactly what went wrong—but it’s not so great for your users, who probably just see scary red text and nothing else. This is where error handling comes in.

With a little planning, we can tell Python:

> “If you run into a problem, don’t crash—here’s how to handle it gracefully.”

We’ll use the `try` and `except` keywords to:

1. Catch specific problems before they stop our program.
2. Give friendly error messages instead of cryptic code dumps.
3. Allow the program to continue running after a hiccup.

Here is an example of the try-except block in action:

```python
try:
    number = int(input("Enter a number to divide 10 by: "))
    result = 10 / number
    print(f"Result is: {result}")
except ZeroDivisionError:
    raise ZeroDivisionError("Oops! You can’t divide by zero.")
except ValueError:
    raise ValueError("That’s not a valid number. Please enter digits only.")
```

In the above block, Python is doing the following:

1. Python tries to run the code inside try:
2. If it hits a `ZeroDivisionError`, it runs the first except block.
3. If it hits a `ValueError`, it runs the second except block.
4. If no errors occur, it skips all except blocks entirely.

In some situations, we might want to let the error pass (that is, we don't want Python to do anything). We can do this using the `pass` statement. However, this is not preferred as Python emphasizes explicitness over implicitness.

# Error handling philosophies

There are actually two camps in programming when it comes to error handling:

## 1. Look Before You Leap (LBYL)

This is the cautious parent approach. You check everything before running the risky code.
All inputs are validated up front. This guarantees a correct outcome (or at least predictable behavior).
The downside is that your code gets verbose because you’re building safety nets everywhere.

## 2. Easier to Ask for Forgiveness than Permission (EAFP)

This is the YOLO teenager approach. You just do the thing, and if it fails, you deal with it after.
You don’t pre-check every possible input or scenario. This often means shorter, cleaner-looking code.
But it can also lead to unpredictable behavior if you haven’t thought through all the ways a user might break your program. The burden falls on you as the programmer to think about what are the many ... ahem... creative way users might break your program (or provide you silly nonsensical values for input)

In short:

- **LBYL** = defensive driving
- **EAFP** = “Let’s floor it and see what happens”

Python tends to favor EAFP because its try/except system is powerful and fast. However, we tend mix both approaches depending on the situation. Personally, I like the LBYL approach if my main routines will take a long time to run. After all, you don't want to spend 1 day running a code only for it to complain about some wrong input values.

## 🧪 Try it: Catch those errors!

Using what you have learned, try to complete the following function:

```python
# TODO: Write the function to handle the following scenarios
# 1. If users provide 0 as an input
# 2. If users provide a string as an input
def reciprocal(x:int) -> str:
  try:
    reciprocal = 1/number
    print (_"Thanks! You entered {number}. The reciprocal is {reciprocal}")
  except ______:
    # Handle zero as an input
    print ("Can't divide by zero!")
  ______ TypeError:
    print (f"Oops! {x} not a number. Try again.")
```

# Conclusion

That’s a wrap on functions — you’re now officially champs at writing reusable, tidy chunks of Python code! 🎉 Functions are your best friends for organizing logic and keeping things neat.

After lunch, we’ll dive into loops — the secret sauce behind making your code repeat tasks over and over without you having to write the same lines again and again. Get ready to unleash the power of automation and save yourself tons of typing!

See you after lunch! 🍴
