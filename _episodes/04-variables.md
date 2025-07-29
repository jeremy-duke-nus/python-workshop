---
title: Variables as data containers in programming
teaching: 30
exercises: 15
questions:
  - How do we store information in Python?
  - How do we modify data?
objectives:
  - Introduce the concept of variables in programming.
  - Highlight rules and best practices in naming variables.
keypoints:
  - Variables are containers used to store data in Python (and all programming languages).
  - We can create, update and destroy variables in Python.
---

# Learning outcomes

In this section, we will dive into variables - a core programming concept in all programming languages.

1. Understand how to use variables, and naming conventions for variables.
2. Create, update and destroy variables in Python.

# The birth of a variable: Variable declaration

Before we dive into data types and other concepts in programming, we will first introduce **variables**.

Variables are ubiquitous in programming. Think of a variable as a container that holds information — like a labeled jar where you can store something for later use. Instead of repeating values over and over, we give them a name and let Python remember them for us.

For example, suppose you want to calculate the area of a circle with radius `5`:

```python
radius = 5
pi = 3.14159
area = pi * radius * radius
print(area)
```

Here, `radius` and `pi` are variables holding values. `area` is another variable that stores the result of a calculation. In important thing to notice here is that we use `=` for assignment. This is a bit unintiutive since we usually think `=` should be testing for equality. We will expound on testing later after lunch.

By using variables, we make our code easier to read, modify, and reuse. If you later decide the circle’s radius should be 10, you only need to change the value of radius instead of rewriting the entire calculation. Variables also offer other advantages, namely:

1. **Readability**: Meaningful naming of variables makes codes easier to understand.
2. **Reusability**: Once a value is stored in a variable, we can re-use it throughout our codes (with exceptions, more on that in Day 1)
3. **Maintainability**: Imagine a value is used tens of times in a code. If we store this value in a variable, we will only need to update it once. This reduces errors should we need to make updates.

{:.callout}

> ## Naming rules: Thou shalt not violate these laws
>
> {:.quote}
>
> > There are only two hard things in Computer Science: cache invalidation and naming things.
> > -- Phil Karlton
>
> Naming of variables is one of the most important, and arguably, one of the hardest thing to do in programming. You need to make sure that the name is informative, not too long, unambiguous... Soon, you will need to find a thesaurus to help with naming your variables (or maybe, generative AI). However, while you are largely free to decide how to name your variables, there are some rules that are enforced:
>
> - **Names must start with a letter or underscore (\_)**
>
> ```python
> name = "Alice"   # valid
> _score = 95      # valid
> 2name = "Bob"    # ❌ invalid (cannot start with a number)
> ```
>
> - **After the first character, names can contain letters, numbers, or underscores**
> - **Names are case-sensitive**
>
> ```python
> age = 25
> Age = 25
> ```
>
> - **No spaces are allowed in names**. Words should be separated by `_` or `.`
>
> ```python
> class number = 35   # ❌ invalid (cannot contain a space in the variable name)
> class_number = 35   # valid
> ```
>
> - **No reserved keywords (words that have special meaning in Python)**
>
> ```python
> class = 35           # ❌ invalid (class is a reserved keyword in Python)
> class_number = 35    # valid
> ```
>
> - **Names cannot contain mathematical symbols**
>
> ```python
> class-number = 35   # ❌ invalid (cannot contain mathematical symbol -)
> class_number = 35   # valid
> ```

Outside of these laws (Python will never let you proceed if you break any of these laws), there are really no hard rules on how to name your variables. However, there are some established **best practices** in the Python community.

{:.callout}

> ## Naming best practices: Some good ideas for your variable names
>
> There are some best practices found in various coding guides, including one from [Google](https://google.github.io/styleguide/pyguide.html) and [PEP8](https://peps.python.org/pep-0008/). I often refer to PEP8 as the holygrail for styling - it is rich in knowledge, yet has a bit of a witty writing style. These two guides not only serve to provide some advice on how to name variables - they provide advice on how you should write codes to make them easy (and I daresay, pleasurable) to read. Some of the best practices are distilled here:
>
> - **Use descriptive names**
>
> ```python
>   student_score, temperature_celsius. # good: self explanatory
>   x, data1, thing                     # ❌ bad: what information is contained?
> ```
>
> - **Follow snake_case for variables and functions**
>
> ```python
>   average_score = 85
>   def calculate_area():
>     pass
> ```
>
> - **Constants are written in ALL_CAPS**
>
> ```python
> PI = 3.14159
> MAX_USERS = 100
> ```
>
> - **Avoid single‑letter names except for simple counters (i, j, k) in loops.**
> - **Choose clarity over brevity**
>
> ```python
> Prefer user_age instead of ua.
> ```
>
> - **Names should not contain data type**.
>
> ```python
> list_of_fruits = ['apple', 'pear'] # ❌ data type should not be provided in the variable name
> fruits = ['apple', 'pear']
> ```

{:.challenge}

> ## Try this
>
> For our project, we will be pulling data from an API URL. This is the URL that we will be using:
>
> ```bash
> https://api-open.data.gov.sg/v2/real-time/api/pm25?date=2025-01-01
> ```
>
> Assign the URL to a suitably named variable.

# Updating variables

# The death of a variable: Destroying variables
