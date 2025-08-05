---
title: How do I compare?
teaching: 20
exercises: 10
questions:
  - How can we make comparisons between values in Python?
  - Truey-ness in Python - what do we mean by True and False?
objectives:
  - Be able to perform basic comparisons in Python
  - Understand what True and False can refer to in Python
keypoints:
  - Booleans are used to reflect the truthiness of a statement in Python.
  - Other than the output of comparisons, booleans are also used to refer to special values (typically empty values)
---

# Learning outcomes

By the end of this lesson, you will be able to:

1. Use Python’s comparison operators (`>`, `<`, `>=`, `<=`, `==`) to test values.
2. Distinguish between assignment (`=`) and equality (`==)`.
3. Recognize how Python uses `True`, `False`, and truthy/falsy values to control program flow.

# Comparisons in Python

Comparisons are a central component of prgrams, and are used extensively to control program flow. Comparisons are performed in Python in a manner similar to how we will write them in mathematics:

```python
35.2 > 35    # True
35.2 >= 35   # True
35.2 < 35    # False
35.2 == 35.2 # True
```

{:.callout}

> ## Equalities in Python
>
> You will notice that we used `==` to compare whether two values are equal. A common mistake people make is to use `=`, which means something else in Python (and most programming langauges). What does `=` do?

While mathematical comparisons (`>`, `<`, `<=`, `>=`) can only used used for numeric data types (including dates), the equality test (`==`) can be used on most data types, including strings, lists, and dictionaries. For example:

```python
[1,2,3] == [1,2,3]  # True
"abc" == "bca"      # False
```

{:.challenge}

> ## Try this
>
> ```python
> # TODO: Fill in the blanks
> # Create two dictionaries
> dictionary1 = __"name": "jeremy"__
> dictionary2 = __"name": "jeremy"__
> dictionary1 __ dictionary2         # True
> ```

# Membership tests

Another class of comparison is that of membership testing. For instance, lets say we have a list of fruits as such:

```python
fruits = ['apple', 'orange', 'banana', 'kiwi']
```

It is a relatively common task to ask if a specific value is in the list (or a string, for that matter). We can quicky do this using the `in` operator. Likewise, negation can be done by adding the `not` operator. For instance:

```python
fruits = ['apple', 'orange', 'banana', 'kiwi']
"apple" in fruits         # True
"pineapple" in fruits     # False

"pineapple" not in fruits # True

"apple" in "pineapple"    # True
"pineapple" in apple      # False
```

Note that in test of membership, casings matter. For instance,

```python
"apple" in "pineapple" # True
"apple" in "pineApple" # False
```

{:.challenge}

> ## How do I do this?
>
> We have seen how `"apple" in "pineapple"` is `True`, but`"apple" in "pineApple"` is `False`. This is by design. However, what can you do if you want to `"apple" in "pineApple"` to also be `True`?

# 🟢 True or False?

When we do a comparison in Python, we will get either `True` or `False` in Python. These special values are called `boolean` types. While `True` and `False` can refer to whether a comparison is true or otherwise, Python takes this further with a concept called **truthiness**. This refers to how certain special values are also considered `True` or `False`. Specifically, empty lists, empty tuples, empty dictionaries and zero will evaluate to False.

{:.challenge}

> ## Try this
>
> Try to check the above statement about truthiness in Python using the following examples:
>
> ```python
> print (bool(0)) # False
> print (bool(1)) # True
> # TODO: Test the truthiness of an empty string, an empty list and an empty dictionary
> ```

# Conclusion

Comparisons and boolean logic are the backbone of decision‑making in programming. In this secion, we have learned how to compare numbers, strings, and even collections, and how Python interprets results as `True` or `False`. With truthiness, Python goes a step further, letting you write clean, natural conditions without extra checks. In the next section, you’ll see how these building blocks let us guide the logic of entire programs.
