---
title: Using libraries to extend Python
teaching: 25
exercises: 5
questions:
  - How do I make use of what others have built in their libraries?
  - What are the best practices in importing libraries?
  - How do I know what a library provides?
objectives:
  - Introduce how libraries work in Python.
  - Using the request library to fetch data from an API.
keypoints:
  - Libraries help extend what we can do in Python without us needing to write more code.
  - We should strive to be selective about what we are importing to reduce namespace conflicts.
---

# Learning outcomes

In this section, we will do the following:

1. Load the `requests` library
2. Fetch the data from the API endpoint using the `requests` library.
3. Understand how to interact with the response from the API.

By the end of this section, you should be familiar with the following:

1. Understand how to load libraries, and best practices on how to do so.
2. Creating new variables to hold information in Python.
3. Make use of `f-strings` to format strings in Python.
4. Fetch data from an API using `requests` and interacting with response from API.

# Working with libraries

Programmers are **lazy** people (as we should be). A fundamental principle we live by (among others) is **Do not repeat yourself**, or DRY. In keeping with this principle, it is a common design pattern for us to write re-usable code to do commonly performed operations.

Python comes installed with a range of libraries (called the `standard libraries`) that will allow us to go about with most of our use cases. Some of these libraries include `requests`, `json`, `datetime`, `os`, `collections` — among a range of others. These are the packages that we will be using in our workshop to work with our API response.

But Python’s power doesn’t stop at its standard libraries. The community has developed a rich ecosystem of third‑party libraries that extend Python’s functionality far beyond its core. These libraries save us from reinventing the wheel — allowing us to leverage the hard work of others while focusing on solving our own problem.

For example, while we’ll use built‑in libraries like `json` to parse data and `datetime` to handle timestamps, we can also make use of external libraries such as:

1. `requests` → a user‑friendly HTTP client for sending API requests
2. `pandas` → for analyzing and structuring tabular data
3. `matplotlib` / `seaborn` → for data visualization

Together, these libraries form a powerful toolkit: `requests` lets us retrieve data from APIs, `json` and `pandas` help us process it, and visualization libraries let us present insights clearly. Installation of most of these packages can be done using `conda` or `pip`, as we had discussed in the previous section.

# Importing libraries

While the Python ecosystem is large, the language is designed to be simple. When you install Python, you only gain access to the standard libraries. Every other package will need to be installed — which, thankfully, has been vastly simplified with package managers.

But what happens if you have installed hundreds of libraries in your environment? Loading all of them every time Python starts up would be slow and memory‑intensive. Instead, we import a library only when we need access to functions in that specific library. Loading a library is akin to telling Python that we want to use a specific tool from a different toolbox. Note that by default, no libraries are loaded when you start Python. Every library that is needed in your program will need to be explicitly imported.

```python
import requests
```

The line above will make classes and functions defined within the `requests` library available for use (**we will come back to what functions etc. are later, but for now, just think of them as pieces of code**). We can import more than one library at a time, if required. For example:

```python
import os
import requests
```

The above lines of code will import both `os` and `requests`.

{:.callout}

> ## Best practices for importing multiple libraries
>
> 1. Imports should be placed at the top of the script file/notebook. This will allow readers to immediately know which packages are needed.
> 2. Imports from the standard library should be listed first, before custom libraries.
> 3. Imports should be listed alphabetically.

There are three methods in which we can load libraries in Python (including the aforementioned method). We will briefly talk about each of them, and how to use them.

- **Standard import**
  This is the most basic of all the import methods. In order to access functionalities provided by the library, we will need to attach the name of the library before the function. For example:

> ```python
> import math
>
> print (math.pi)
> ```

- **Aliasing**

This is similar to the **standard import**; however, this allows us to shorten the name of the libraries when we are referring to functions from it. For example, we can use the following to get the value of `pi`:

> ```python
> import math as mt
>
> print (mt.pi)
> ```
>
> This is useful when the library name is really long, and you are going to be referring to it often. Some common patterns you will see in the wild include:
>
> ```python
> import numpy as np
> import pandas as pd
> import tensorflow as tf
> ```

- **Selective import**
  Here, you will only import functions you need. This allows us to call a function directly without providing the name of the library.

> ```python
> from math import pi
> print (pi)
> ```
>
> However, this comes at a risk of **namespace conflicts**

{:.callout}

> ## Namespaces
>
> A namespace is a mapping from names to objects. It functions like a dictionary where keys are object names (identifiers) and values are the objects themselves. Namespaces provide a mechanism to organize and manage identifiers, preventing naming conflicts and ensuring that each name refers to a unique object within its specific context. Python uses namespaces: a system that keeps names organized so that functions from different libraries don’t accidentally overwrite each other. For example:
>
> ```python
> import math
> import cmath
>
>
> print(math.sqrt(25)) # square root from the math library
> print(cmath.sqrt(-25)) # complex square root from the cmath library
> ```
>
> Both `math` and `cmath` expose the function `sqrt`; however, the implementation of `sqrt` in `math` does not allow us to work with complex numbers. By explicitly mentioning which library's implementation we are using, we are unambiguous in the expected behavior of our code.

{:.challenge}

> ## Try it yourself
>
> Load the following packages: `json`, `datetime` into your notebook.

# Conclusion

In this section, we have introduced how libraries can be used to extend the functionality of Python. In the next section, we will be performing our first API query to fetch data. This will also be your first encounter with some core data types in Python. The next section will be an extremely important section for your Python journey!
