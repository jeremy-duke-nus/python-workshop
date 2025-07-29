---
title: Fetching data from an API
teaching: 30
exercises: 30
questions:
  - How do I make use of what others have built in their libraries?
  - What are the best practices in importing libraries?
  - How do I know what a library provides?
objectives:
  - Introduce how libraries work in Python.
  - Using the `request` library to fetch data from an API.
  - Explore the content of an API response.
keypoints:
  - Libraries helps extend what we can do in Python without us needing to write more codes.
  - We should strive to be selective about what we are importing to reduce namespace conflicts.
---

# Learning outcomes

In this section, we will do the following:

1. Load the `request` library
2. Fetch the data from the API endpoint using the `request` library.
3. Understand how to interact with the response from the API.

By the end of this section, you should be familiar with the following:

1. Understand how to load libraries, and best practices on how to do so.
2. Creating new variables to hold information in Python.
3. Make use of `f-strings` to format strings in Python.
4. Fetch data from an API using `request` and interacting with response from API.

# Working with libraries

Programmers are **lazy** people (as we should be). A fundamental principle we live by (among others) is **Do not repeat yourself**, or DRY. In keeping with this principle, it is a common design pattern for us to write re-usable codes to do commonly performed operations.

Python comes installed with a range of libraries (called the `standard libraries`) that will allow us to go about with most of our use cases. Some of these libraries include `requests`, `json`, `datetime`, `os`, `collections` - among a range of others. These are the packages that we will be using in our workshop to work with our API response.

But Python’s power doesn’t stop at its standard libraries. The community has developed a rich ecosystem of third‑party libraries that extend Python’s functionality far beyond its core. These libraries save us from reinventing the wheel — allowing us to leverage the hard work of others while focusing on solving our own problem.

For example, while we’ll use built‑in libraries like `json` to parse data and `datetime` to handle timestamps, can also make use of external libraries such as:

1. requests → a user‑friendly HTTP client for sending API requests
2. pandas → for analyzing and structuring tabular data
3. matplotlib / seaborn → for data visualization

Together, these libraries form a powerful toolkit: `requests` lets us retrieve data from APIs, `json` and `pandas` help us process it, and visualization libraries let us present insights clearly. Installation of most of these packages can be done using `conda` or `pip`, as we had discussed in the previous section.

# Importing libraries

While the Python ecosystem is large, the language is designed to be simple. When you install Python, you only gain access to the standard libraries. Every other package will need to be installed - which, thankfully, ihas bee vastly simplified with package managers.

But what happens if you have installed hundreds of libraries in your environment? Loading all of them everytime Python starts up will be slow and memory-intensive. Instead, we will have to import a library when we need access to functions in a specific library. Loading a library is akin to telling Python that we want to use a specific tool from a different toolbox. Note that by default, no libraries are loaded when you start Python. Every library that is needed in your program will need to be explicitly imported.

The package we will be working with here is `requests`, which as its name implies, is meant to make web requests. We will use the following line of code to import the library:

{:.code}

```
import requests
```

The line above will make classes and functions defined within the `requests` library available for use (**we will come back to what functions etc are later, but for now, just think of them as pieces of codes**). We can import more than one library at a time, if required. For example:

{:.code}

```
import os
import requests
```

{: .callout}

> # Best practices for importing multiple libraries
>
> There are a few best practices for importing multiple libraries. These includes the following:
>
> 1. Imports should be placed at the top of the script file/notebook. This will allow readers to immediately know which packages are needed.
> 2. Imports from the standard library should be listed first, before custom libraries.
> 3. Imports should be listed alphabetically.

# Namespaces

When a library gets imported, what happens under the hood is that Python gains access to all the functions etc defined within that package. However, what can happen is that sometimes, the same function name is used by multiple packages. This is called a **namespace conflict**. To avoid such issues, Python uses namespaces: a system that keeps names organized so that functions from different libraries don’t accidentally overwrite each other.

{: .callout}

> # Namespaces
>
> a namespace is a mapping from names to objects. It functions like a dictionary where keys are object names (identifiers) and values are the objects themselves. Namespaces provide a mechanism to organize and manage identifiers, preventing naming conflicts and ensuring that each name refers to a unique object within its specific context.
