---
title: Fetching data from an API
teaching: 60
exercises: 15
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

# Expected outcomes

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
