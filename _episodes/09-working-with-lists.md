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
