---
title: Deciding an appropriate course of action in my program flow
teaching: 30
exercises: 30
questions:
  - How can we make a program decide how to process an input?
objectives:
  - Understand the structure of a program that applies conditional logic to perform different tasks
keypoints:
  - The `if`-`elif`-`else` block is a fundamental concept in all programming languages.
  - Since Python 3.10, we can also use `match` to manage program flow.
---

# Learning outcome

In this section, we will learn:

1. How to make use of conditional logic to control program flow.
2. Use `match` for structural matching to control program flow.

# 🌱 Conditional Logic in Python

Imagine you’re planning a data. If it’s sunny, you’ll take your date to the beach for a stroll. If it looks cloudy, you'll take your date to Gardens By The Bay. Otherwise, you will take your date to the shopping mall.

That decision‑making process is conditional logic, and in Python, we write it using `if‑elif‑else` blocks.
They allow your program to make choices and take different paths depending on the situation. Instead of running the same steps every time, your code can react intelligently to different conditions.

To do this, we will make use of `if-elif-else` blocks. In this section, we will go through how this can be set up. We will wrap up this section (and the day) by introducing the `match` case that was introduced in the later versions of Python. With these tools, your Python programs will stop being static scripts and start becoming flexible, decision‑making machines.

# 📏 Tabs, Spaces, and Why They Matter

So far, the Python code we’ve written has been single‑line commands. But now that we’re learning conditional logic, we’ll need to group blocks of code that only run under certain conditions.

In many programming languages, you might see `{curly braces}` or other symbols marking these blocks.
But in Python, we use something much simpler — indentation (tabs or spaces).

Think of indentation as Python’s way of knowing what belongs inside a block.

```python
if True:
    print("This line is inside the block")
    print("So is this one")
print("But this one is outside")
```

👉 Notice that the first two print statements are indented with four spaces.
That indentation tells Python:

- These lines belong to the if condition.
- When the if is True, run them together.

If you forget the spaces, Python will get confused — and remind you with an `IndentationError`.

{:.callout}

> ## 💡 Pro tip
>
> Use 4 spaces for indentation in Python (not the Tab key — though most editors will insert spaces automatically). This is because the `Tab` key can be interpreted differently, depending on your computer and your editor. However, most modern editors such as VSCode will automatically insert 4 spaces instead of `Tab`.

# Writing your first conditional flow

Remember our motivating example at the start of this episode: **deciding where to take our date, depending on the weather**. Conditional logic in Python allows us to write code that makes decisions — just like we do in real life.
Let’s see how our decision‑making translates into Python:

```python
weather = "sunny"

if weather == "sunny":
  print ("Lets go to the beach")
elif weather == 'cloudy':
  print ("Lets go to Gardens By The Bay")
else:
  print ("Lets go shopping")
```

Here’s what’s happening:

- Python first checks the condition after the if.
- If that condition is true, the indented block runs.
- If not, Python moves on to the next condition (elif, short for else if).
- If none of the conditions match, the else block acts as a fallback.

This way, Python helps us create programs that behave differently under different circumstances — just like real‑world decisions. Note that you can use as many `elif` conditions as you deem necessary, but you can only have one `else` clause (since it is supposed to be the 'default' action to take).

{:.challenge}

> ## Try this
>
> Using conditional logic, print out whether a given country is in Asia, Europe or North America:
>
> ```python
> #TODO: Fill in the blanks
>
> asia = ['singapore', 'japan', 'korea', 'indonesia', 'thailand']
> europe = ['italy', 'france', 'germany', 'russia']
> north_america = ['canada', 'mexico', 'united states']
>
> country = 'france'
> __ country __ asia:
>     print (_"{country} is in Asia")
> __ country ___ europe:
>     print (_"{country} is in Europe")
> __ country ___ north_america:
>     print (_"{country} is in North America")
> ______:
>     print ("I am not sure where this country is in.")
>
> # Output: "france is in Europe"
> ```

{:.challenge}

> ## What is going on?
>
> What went wrong in the following code block?
>
> ```python
> #TODO: Fill in the blanks
>
> asia = ['singapore', 'japan', 'korea', 'indonesia', 'thailand']
> europe = ['italy', 'France', 'germany', 'russia']
> north_america = ['canada', 'mexico', 'united states']
>
> country = 'france'
> if country in asia:
>     print (f"{country} is in Asia")
> elif country in europe:
>     print (f"{country} is in Europe")
> elif country in north_america:
>     print (f"{country} is in North America")
> else:
>     print ("I am not sure where this country is in.")
>
> # Output: "I am not sure where this country is in."
> ```

# Common design patterns

`if-elif-else` blocks are ubiquitous in Python programming. These are some common design patterns commonly encountered:

{:.callout}

> ## 1. Single Decision (If‑Else)
>
> The simplest form: two possible paths.
>
> ```python
> age = 20
> if age >= 18:
>     print("You can vote!")
> else:
>     print("You are too young to vote.")
> 💡 Pattern: “Yes/No” or “This or That” decisions.
> ```

{:.callout}

> ## 2. Multiple Exclusive Choices (If‑Elif‑Else Chain)
>
> Use when only one condition should run.
>
> ```python
> grade = 85
>
> if grade >= 90:
>     print("A")
> elif grade >= 80:
>     print("B")
> elif grade >= 70:
>     print("C")
> else:
>     print("D or below")
> 💡 Pattern: Tiered decision‑making (ranking, thresholds).
> ```

{:.callout}

> ## 3. Cascading Checks with a Fallback
>
> Check multiple possibilities, but always end with a safe “else”.
>
> ```python
> weather = "rainy"
>
> if weather == "sunny":
>     print("Go hiking!")
> elif weather == "cloudy":
>     print("Visit a museum.")
> elif weather == "rainy":
>     print("Watch a movie at home.")
> else:
>     print("Stay flexible!")
> ```
>
> 💡 Pattern: Default behavior if no earlier condition matches.

{:.callout}

> ## 4. Nested Conditions
>
> Sometimes decisions depend on two or more layers of logic.
>
> ```python
> age = 16
> has_id = True
> if age >= 18:
>     if has_id:
>         print("Entry allowed")
>      else:
>         print("Bring your ID next time!")
> else:
>     print("Sorry, you must be 18 or older.")
> ```
>
> 💡 Pattern: Layered logic, though can get messy quickly. Use this with caution. It is usually the case that if you have too many layers of tests, you can probably simplify that logic.

{:.callout}

> ## 5. Many Equalities (Candidate for Pattern Matching)
>
> When you’re checking the same variable against many values.
>
> ```python
> day = "Saturday"
>
> if day in ["Saturday", "Sunday"]:
>     print("Weekend!")
> elif day in ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]:
>     print("Weekday!")
> ```
>
> 💡 Pattern: Repeated comparisons — this is a prime candidate for Python’s match statement (structural pattern matching), which we’ll explore soon.

# Structual matching in Python

Sometimes, our `if‑elif‑else` chains can get a little long and messy — especially when we’re checking the same variable against many possible values (see **Common Design Pattern 5**). Starting from Python 3.10, we have a cleaner and more powerful way to handle this: the `match` statement.

Think of `match` as Python’s version of a “switch” statement (like in other languages), but with superpowers: it not only checks values but can also unpack structures like lists, dictionaries, and even custom objects.

Here’s a simple example to see how it works:

```python
day = "Saturday"

match day:
    case "Monday" | "Tuesday" | "Wednesday" | "Thursday" | "Friday":
        print("It’s a weekday!")
    case "Saturday" | "Sunday":
        print("It’s the weekend!")
    case _:
        print("Not a valid day!")  # The underscore (_) is the "catch-all"
```

**💡 What’s happening here?**

- We tell Python: “Look at the value of day.”
- Each case checks if it matches a possibility.
- `|` means “or,” so one case can cover multiple values.
- `_` is a special placeholder that matches anything (like a default fallback).

**Why use match instead of if‑elif‑else?**

- ✅ Cleaner and easier to read when checking many possibilities.
- ✅ Can handle complex data structures (beyond simple values).
- ✅ Avoids repeating if conditions over and over.

However, the `match` is not only limited in testing for whether a value is in a list (as we saw above). It is also capable of handling more complex structures, as we will see next.

# Pattern Matching with Unpacking

`match` doesn’t stop at simple values — t can also unpack data structures like tuples and lists while checking their contents. This makes it super handy for scenarios like working with coordinates or structured data.

To highlight what we mean, lets use the example of a 2D point (x, y):

```python
point = (0, 5)

match point:
    case (0, 0):
        print("Origin")
    case (0, y):
        print(f"On the Y-axis at y={y}")
    case (x, 0):
        print(f"On the X-axis at x={x}")
    case (x, y):
        print(f"Somewhere else: x={x}, y={y}")
```

**🔍 What’s happening here?**

- `(0, 0)` matches exactly the origin.
- `(0, y)` matches any point on the Y-axis, capturing the y value.
- `(x, 0)` matches any point on the X-axis, capturing the x value.
- `(x, y)` is the fallback — it captures any other coordinate.

So if point = (0, 5), the output will be:

```python
On the Y-axis at y=5
```

This way, match doesn’t just tell us what was matched — it can also extract values directly into variables while doing so.

{:.challenge}

> ## Try this: Sorting a Mail Item
>
> A mail item arrives at your desk in the form of a tuple:
>
> ```python
> mail = ("package", "Alice")
>
> # Instructions: Use match with unpacking to decide what message to print:
> # TODO: Fill in the blanks
>
> mail = ("package", "Alice")
>
> ____ mail:
>     ____ ("package", ____):
>         print(f"Delivering a package to {receipient}")
>     ____ ("letter", recipient):
>          print(________)
>     ____ ("postcard", recipient):
>          print(f"Delivering a postcard to {recipient}")
>     ____ (_, recipient):
>          print(f"Don’t know what to deliver to {recipient}!")
> ```
>
> Change mail to ("letter", "Bob"). What happens?
> Add a new rule for "magazine".
> Try changing the last case so that it prints "Unknown item" without mentioning the recipient.

{:.challenge}

> ## Try This
>
> This is an exercise for you to exercise your new programming chops:
> Imagine you are building a simple command interpreter that reacts differently based on the user’s input command stored in the variable command:
> `command = "play"`
> Your task is to write a control flow that:
>
> 1. Prints "Playing music" if command is "play"
> 2. Prints "Pausing music" if command is "pause"
> 3. Prints "Stopping music" if command is "stop"
> 4. Prints "Unknown command" for anything else
