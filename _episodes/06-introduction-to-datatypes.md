---
title: Introduction to data types
teaching: 25
exercises: 15
questions:
  - What are data types?
  - Why does the data type matter?
  - How do we work with text in Python?
objectives:
  - Introduce core data types in Python.
  - Describe how Python understands how to process a piece of data.
  - Perform simple operations involving the formatting of strings.
keypoints:
  - How Python performs operations depends on the data type.
---

# Learning outcomes

In this section, we will do the following:

1. Discuss data types and why Python cares about them.
2. Perform common operations involving strings.

{:.callout}

> ## Previously...
>
> In the previous section, we created a variable containing the URL of the API we will be working with for the workshop. It was mentioned that you need to encapsulate the URL within quotes. In this section, we will talk about data types and how Python makes sense of them.

# Introduction to data types

When we write programs, we often work with different kinds of information — text, numbers, lists of items, and more. Python needs a way to distinguish between these kinds of information so it knows how to handle them. That’s where data types (or **class**, I will use them interchangeably here) come in. A data type tells Python what kind of value a variable is storing and, as a result, what you can do with it. For example, text like our API URL is stored as a string, while whole numbers are stored as integers, and decimal numbers as floats. Understanding data types helps us use variables correctly and avoid errors when performing operations.

# Data types and class methods

In Python, everything — including the URL we stored earlier — is an object. This is because Python is built around the principles of **object-oriented programming (OOP)**. In OOP, objects bundle together both data (the value itself) and behaviors (functions, called methods, that can be performed on that data).

For example, the URL we wrote inside quotes is recognized as a string object. That means it’s not just raw text — it comes with built-in behaviors, such as the ability to change its case (`.upper()`), check its length (`len()`), or see if it contains certain words ("api" in url).

So when we talk about data types in Python, we’re really talking about the different classes of objects that Python provides, such as strings, integers, floats, and lists. Each data type is defined by a class, and every variable we create is an instance of one of these classes. Understanding this helps us see why data types behave the way they do and how we can use them effectively.

A key aspect of data types is that they can implement the same operation in different ways. Here’s an example:

```python
sum_of_strings = "1" + "2"
sum_of_numbers = 1 + 2

print (sum_of_strings)
print (sum_of_numbers)
```

In this example, we’re using the same operation (`+`), which corresponds to the special method `__add__`. But notice how the results differ:

- For strings, `+` means concatenation (joining text together).
- For numbers, `+` means addition in the mathematical sense.

This illustrates how Python’s object-oriented nature allows different data types to provide their own implementations of the same operation, making the language both powerful and flexible. It also highlights why it’s essential to understand the data types we’re working with: as data flows through a program, its type determines how Python interprets operations, which in turn shapes the results we get.

# Type coercion

There are various data types in Python. The core ones we will be going through in this workshop are string (`str`), numbers (integers - `int` and decimals - `float`), date (`datetime`), dictionary (`dict`), lists (`list`), tuples (`tuple`), boolean (`bool`), None (`None`) and set (`set`). There are a few other data types which I find to be helpful that builds on these core types: `Counter` (which builds on `set`), `defaultdict` (which build on `dictionary`), `namedtuple` (which builds on `tuple`) that provide a bit more functionality than those implemented in the base class. We will however not be going through these extended classes, since we do not need to use them for purpose.

But what if you need to convert data between compatible types?

{: .challenge}

> ## Try it
>
> Consider the following example of a simple calculator program which prompts users for a numeric input:
>
> ```python
> first_number =input("Provide the first number: ")
> next_number =input("Provide the next number: ")
> ```
>
> What are `first_number` and `next_number` respectively stored as?

Here's where **type coercion** comes in.

By default, the `input()` function always returns a string, no matter what the user types. So even if a user enters `7` or `42`, those values are stored as "7" and "42", not as numbers.

If we try to add them directly, Python treats them as strings:

```python
print (first_number + next_number)
```

This is entirely consistent with what Python **thinks** we mean because it thought we provided it two strings for addition. We know better, as we are expecting a mathematical addition. In order to force Python to treat `first_number` and `next_number` as numbers, we will need to perform type coercion, as below:

```python
first_number = int(first_number)
next_number = int(next_number)

result = first_number + next_number
print("Result:", result)
```

{:.callout}

> ## Determining the type of a variable
>
> We can determine the type of a variable using the function `type`. For instance, `type (first_number)` will tell us that `first_number` is a variable of `<class str>`

For the next few minutes, try to explore a few type coercions on your own.

{: .challenge}

> ## Try it
>
> Use the following variables:
>
> ```python
> string = "1"
> number = 1.30
> boolean = True
> example_list = [1,2,3,4]
> example_tuple = (1,2,3,4)
> ```
>
> Try to perform type coercions between as many types as you can. What type conversions worked? And which did not?

# With great powers come great responsibility

The ability to perform type coercion makes Python a really friendly language, but this comes with a few trade‑offs. For example:

1. **Flexibility** vs. **Safety**: Python will happily convert between compatible types when asked, but it assumes you know what you’re doing. If you try to convert `"hello"` into an integer, you’ll get a `ValueError`.
2. **Implicit** vs. **Explicit** Behavior: While some languages perform a lot of automatic coercion, Python generally requires explicit conversion (e.g., `int("42")`). This reduces hidden bugs but means you need to pay closer attention to data types.
3. Performance Costs: Coercing between types repeatedly can slow down a program, especially when working with large datasets. This is one of the reasons why strongly typed languages such as `C++` are significantly faster.

So while type coercion is a powerful feature that makes Python easy to use and beginner‑friendly, it also places responsibility on you as the programmer to ensure that your data is valid and being used in the right way. We will talk more about validation later in the workshop.

# Strings as assemblage of characters

Now that we have introduced data types, let's go through strings. Strings are the most commonly used data type in programming because they allow us to work with text.
A string is simply a sequence of characters enclosed in either single quotes ('), double quotes ("), or sometimes triple quotes (''' or """) for multi-line text.
Most of these methods for strings concern themselves with formatting. For example:

```python
name = 'jeremy ng'
upper_cased = name.upper()         # Converts whole name to upper case
capitalized = name.capitalize()    # Converts only the first letter of each word to upper case
lower_cased = upper_cased.lower()  # Converts the whole string back to lower case

len(name)                          # Returns the number of characters in a string
```

What if we need to dynamically generate a string?

Imagine you’re building a program that greets users. This is how we **can** do it.

```python
name = "Alice"
age = 25
print("Hello " + name + ", you are " + str(age) + " years old.")
```

While it works, this is messy and simply not scalable. This also makes our code error-prone. Instead, we can use **string formatting**. String formatting allows us to create templates with placeholders and then insert values into them. It makes your code cleaner, more readable, and flexible. There are three ways which string formatting can be done in the newer versions of Python.

{:.callout}

> ## f-strings
>
> This is the most modern method only available in **Python 3.6** onwards.
>
> ```python
> name = "Alice"
> age = 25
> print(f"In five years, {name} will be {age + 5} years old.")
> ```
>
> This is the most preferred option because this is
> ✅ Easy to read
> ✅ No need to convert numbers manually
> ✅ You can even use expressions

{:.callout}

> ## format
>
> This is my preferred method in Python 2.
>
> ```python
>
> print("Hello {}, you are {} years old.".format(name, age))
> ```

> You can also use placeholders with positions:
>
> ```python
> print("Hello {0}, in two years you’ll be {1}.".format(name, age + 2))
>
> ```

{:.callout}

> ## `%` method
>
> This is rarely used today, but might still be seen in legacy codes.
>
> ```python
> print("Hello %s, you are %d years old." % (name, age))
> ```
>
> Notice in this method that there is a character (`s` or `d`) next to the `%`. This character is important as it tells Python what is the class of data to be injected into the template for rendering.

{:.challenge}

> ## Try it
>
> Try using string formatting to generate the URL we will be querying later
>
> ```python
> # TODO: Fill in the blanks to generate the full URL
> date = "2025-01-01"
> base_url = "https://api-open.data.gov.sg/v2/real-time/api/twenty-four-hr-forecast"
>
> full_url = f"{_____}?date={_____}"
> print(full_url)
> ```
>
> Try to also perform the same using format and `%`. The exercise notebook also provides some other worked exercises for you to practice string formatting. Go through these exercises in the next few minutes.

# Conclusion

Up to this point, we have been introduced to some basic concepts in Python. We have also discussed strings, and generated the URL of an API endpoint which we will be querying later. After lunch, we will perform our first API query.
