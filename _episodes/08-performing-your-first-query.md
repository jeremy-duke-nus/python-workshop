---
title: Performing your first API query
teaching: 20
exercises: 20
questions:
  - How can we perform our first API query?
  - How do we interact with the response we get back from the API?
objectives:
  - Perform your first API query using Python.
  - Understand how to interact with the response you get back from the API.
  - Be able to create and manipulate JSON objects.
  - Learn how to handle common errors anticipated working with JSON objects.
keypoints:
  - A JSON is represented internally as a dictionary, a type of data structure with key-value pairs.
  - Dictionaries are used frequently for storing values which we will need to retrieve rapidly.
---

# Learning outcomes

By the end of this section, you should be able to:

1. Make use of the `request` library to query an API
2. Interact with a response object to interrogate the status codes and response
3. Extract the query result (`body`) from the API response,
4. Perform basic dictionary operations

{:.callout}

> ## Previously
>
> Previously, you had used string formatting to generate the URL for the API. For the purposes of standardization in this section, we will create a new variable with the URL as follows:
>
> ```python
> url = "https://api-open.data.gov.sg/v2/real-time/api/twenty-four-hr-forecast?date=2025-01-01"
> ```

Now that you've become masters of crafting URLs using string formatting, it's time to actually send those URLs off into the digital world and bring back meaningful data.

You'll dive into using the powerful `requests` library to communicate with APIs, explore how to check if your requests were successful by examining status codes, and unlock the gold mine of data contained in the API response (if the query was successful!). Along the way, you'll get comfortable manipulating the returned data using Python's handy dictionary operations.

By the end, you'll be confidently turning your URLs into actionable insights — ready to tap into a whole universe of APIs!

# Interfacing with APIs in Python

While you can query an API by providing the APIs URL in the search bar, this is not scalable since someone needs to paste the URL, send the request, and copy the response somewhere for processing. Instead, we can do this directly in Python using `requests`.

{:.callout}

> ## Python interfaces for HTTP operations
>
> There are two popular libraries you can use for interfacing with APIs: `requests` and `urllib3`. We will be using `requests` because it is easier. On the other hand, `urllib3` is a lower-level library that exposes a lot more functionalities, making it more powerful option. In fact, `requests` actually builds on `urllib3` but remove many of the options by setting sensible default behaviours. If you are interested in building and customizing your requests, it will be worth looking at `urllib3` later.

As you can already guess, the first thing we will need to do is to load the `requests` library.

{:.challenge}

> ## Simple revision
>
> How do you load the `requests` library?

# Sending your first query and receiving your first response

{:.callout}

> ## Pro Tip ⚡
>
> If you are not sure what methods are available for an object, you can simply pass the object into the `dir` function. This will give you a list of all the methods and attributes available in the object.

# Dictionaries: Powerful data type for fast look ups.

# Conclusion

Congrats on finishing this exercise! 🎉 This is one small step into the world of working with APIs, but a big huge step for you in your programming journey. With your new skills in sending requests, checking responses, and handling data, you’re ready to unlock tons of powerful tools and information online 🚀. But how can we begin to manipulate the data fetched back from the API?
