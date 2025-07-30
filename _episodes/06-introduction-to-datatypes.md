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

When we write programs, we often work with different kinds of information — text, numbers, lists of items, and more. Python needs a way to distinguish between these kinds of information so it knows how to handle them. That’s where data types come in. A data type tells Python what kind of value a variable is storing and, as a result, what you can do with it. For example, text like our API URL is stored as a string, while whole numbers are stored as integers, and decimal numbers as floats. Understanding data types helps us use variables correctly and avoid errors when performing operations.

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
