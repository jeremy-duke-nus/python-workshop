---
title: Manipulating a collection of records
teaching: 20
exercises: 30
questions:
  - What are some common data types used to store collections of items?
  - How can we manipulate the data in these collections?
objectives:
  - Understand the differences between a list and a tuple.
  - Be able to create, update and subset a list.
keypoints:
  - While both lists and tuples are used to store collections, they differ in mutability.
  - We can use slicing to subset values within a collection.
  - Unpacking allows us to assign multiple elements to multiple variables simultaneously.
---

# Learning outcomes

By the end of this section, we should be:

1. Familar with lists and tuples,
2. Be able to slice, subset and edit lists.

# Most data are collections of values

So far, we’ve been looking at data that comes as a dictionary — like a phone book where each label (or key) points to one piece of information.

But what if a label points to more than one thing? For example, imagine asking an API for a list of all the tasks a user has. Instead of giving you just one task, it sends back a list of tasks. In Python, we call this a list — it’s like a shopping list, a to‑do list, or a playlist: an ordered collection of items. You can look at the first item, the second, the third, and so on.

Returning to your example API call before, lets take a look at the records that are contained in this response

```python
URL = "https://api-open.data.gov.sg/v2/real-time/api/twenty-four-hr-forecast?date=2025-01-01"

response = requests.get(URL)
forecast = response.json()

# To get the data, contained in the data key
data = forecast['data']
print (data.keys())

# Records, which are found in the records key.
records = data['records']
print (records)
```

There are in fact 6 different measurements that were taken. We can confirm this by finding the length of a list. This is done as follows:

```python
len(records)
```

A list in Python is defined as anything that has a length of zero or more. Let's dive a bit more into lists in Python, including how to create them and later, how do we work with them.

# Working with lists

Just like how an empty notebook is still a notebook, we can always create an empty list by doing the following:

```python
empty_list = []
```

{:.challenge}

> ## Methods in lists
>
> Try to get the list of methods and attributes that are available for working with lists first.

To find the length of a list, we can do (unsurprisingly) `len`. For instance,

```python
len(records)
```

tells us there are 6 records in the list.

# Surprise, surprise!

Here's an interesting exercise. Let's create a list `list1`, and we create a second list that is the same as `list1` as `list2`, as follows:

```python
list1 = ["A", "B", "C"]
list2 = list1
```

Now, we decided that we will now add a new value to `list1`.

{:.challenge}

> ## Try it
>
> Update `list1` by adding "D" to the last entry. How will you do this?
> 🔍 We will append "D" to the list.

Now, you will expect `list1` to be `["A", "B", "C", "D"]` while `list2` is `["A", "B", "C"]`, right? Try this:

```python
print (list1)
print (list2)
```

What do you see 🔍 ? Somehow, although you only changed `list1`, the change also affected `list2` . But why? To understand this, we will need to go back again to variables. But this time, we will peel under the hood to understand what is happening.

# Variables are really pointers to memory locations

The figure below shows what happens under the hood when we create a new variable.

![Figure showing how Python treats variables](figs/variable-memory-assignment.jpg)

When a variable is created, Python stores the value in the memory. However, the variable itself is a pointer to the memory location, not to the value. That is, the variable actually says "this is where this piece of data is found at", rather than "this is what this piece of data is". When we created `list2` by saying `list2 = list1`, what we actually told Python is "`list2` shares the same address as `list1`".

{:.challenge}

> ## Further prove of variables and memory
>
> To convince yourself, try the following:
>
> ```python
> list1 = [1,2,3]
> list2 = list1
> list3 = [1,2,3]
> print (list1 is list2)
> print (list1 is list3)
> ```
>
> What do you see?

Lets say you want to create `list2` with the exact same values as `list1`, but not want them to share the same memory address (as will be the case if we used `=`). You will need to do a **deep copy**, which is in contrast to a **shallow copy** that is done using `=`. In shallow copy, only the pointer is copied. On the other hand, a deep copy copies the values to a new address. This can be done as follows:

```python
list1 = [1,2,3]
list2 = list1.copy()
```

{:.challenge}

> ## Try this
>
> Verify that `list2` created using the method described above does not share the same memory as `list1`. Do this by (1) updating `list1` and then printing the values of both lists, and (2) using the `is` operator.

# 🔎 How to Obtain Specific Values in a List

A list is like a row of numbered mailboxes. Each mailbox has a number, and you can open the one you want to see what’s inside. In Python (as with other languages), these numbers are called **indexes**.

👉 Important: Python starts counting at 0, not 1.

That means the first item is at position 0, the second at 1, and so on. We can access specific values based on their positions in the list using the `[]` operator as shown below:

```python
shopping_cart = ['apple', 'cheese', 'flank steak', 'chicken thighs', 'vegetables', 'bread']

shopping_cart[0]     # apple
shopping_cart[1]     # cheese
```

{:.callout}

> ## A note on indexing
>
> You will often hear programming languages discribed as zero or one-indexed, and open or closed ranges. It is **very** important to know which system is used by your programming language. Python uses a zero-indexed, open-ranged coordinate system. Here's what this means:
>
> {:.challenge}
>
> > ## 🔹 Zero‑Indexed vs. One‑Indexed
> >
> > This means the first position is to be zero. This is common among programming languages. In a one-indexed coordinate system, we will need to use `shopping_cart[1]` to get the first value in the list.
>
> {:.challenge}
>
> > ## 🔹 Open vs. Closed Ranges
> >
> > Range is a sequence of numbers used for tracking. The difference between open and closed ranges is that in an open-ended system, the last number is not included in the counting. For example: `shopping_card[0:3]` will return the first 3 items and not the 4 (index position 3 corresponds to the fourth entry in the list).
>
> It can be really confusing what to indicate as the ranges. I personally use this formula: `[start: start + number of entries ]`. This is one of the consequence of the open-ended range: when you subtract the end index from the start index, you will get back exactly the number of elements requested.

Lets say we want to get the first three elements of the list. We can do this as follows:

```python
shopping_cart = ['apple', 'cheese', 'flank steak', 'chicken thighs', 'vegetables', 'bread']

shopping_cart[0:3]     # ['apple','cheese','flank steak']

# The above can be simplified as follows:
shopping_cart[:3]
```

By default, if you do not supply the start value, Python assumes you want to get everything starting from the first value. Similarly, if you did not define the ending index, Python assumes you want to slice to the last value.

{: .challenge}

> ## Try this
>
> Try to do the following slicing exercises
>
> ```python
> # Our sample list
> animals = ["cat", "dog", "rabbit", "parrot", "hamster"]
> print ("The full list:", animals)
> # Try these:
> print ("First animal:", animals[_])      # should print "cat"
> print ("Third animal:", animals[_])      # should print "rabbit"
> print ("All animals from rabbit to the end:", animals[])
> ```

You can also specify negative index values. For example, if we want to obtain the last 3 values:

```python
animals[-3:]
```

Finally, we can specify **step sizes** as follows:

```python
animals[::2] # ['cat', 'rabbit', 'hamster']
```

Combining these characteristics together, how can we reverse a list?

# Sorting a collection
