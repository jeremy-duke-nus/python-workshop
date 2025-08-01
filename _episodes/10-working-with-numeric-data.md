---
title: Working with numeric and time data in Python
teaching: 20
exercises: 10
questions:
  - What are the different numeric types in Python?
  - How can we work with date and time in Python?
  - How can we properly format our numeric data?
objectives:
  - Understand the difference between floats and integers in Python.
  - Be able to perform common mathematical operations in Python.
  - Be familiar with the representation of date and time in Python using the `datetime` libary.
  - Be able to properly format numbers, dates and time in Python.
keypoints:
  - Floats and integers differ in accuracy, with floats storing up 15-17 decimals points only.
  - We can use string formatting or round to format numbers.
  - The datetime module provides us handy ways to work with dates and times.
---

# Learning outcome

In this section, we will:

1. Differentiate between integers, floats, and dates in Python.
2. Perform basic arithmetic with numbers (adding, subtracting, multiplying, dividing).
3. Understand precision: when to use an integer vs. a float.
4. Work with dates and times using Python’s datetime library.
5. Convert between types when needed (e.g., turning text into numbers or dates).

# Introduction

So far, we’ve been working with lists — collections of values we can slice, sort, and unpack. But if you think about it, many of the items in those lists were numbers: counts, measurements, coordinates. And sometimes, we’ll also see dates or times, which are just as important when working with real‑world data.

👉 In Python, not all data is the same. A “3” can mean very different things depending on whether it’s:

1.  the number of items in your shopping cart (integer),
2.  the weight of an apple in kilograms (float), or
3.  the 3rd day of the month (date).

To handle these differences, Python gives us different data types designed for different purposes.

# Numeric data types

When you see the the number 3 and 3.0, you will instinctively recognize them to be the same. However, this is not the case in Python.

👉 In Python, 3 is an integer (`int`), while 3.0 is a floating‑point number (`float`).

- An integer is a whole number — no fractions, no decimal point.
- A float is a number with a decimal point, even if the decimal part is zero.

Why does this matter? Because Python treats them differently under the hood:

```python
float(1.0001) == float(1.0) # False
int(1.0001) == float(1.0)   # True
int(1.001) == int(1.0)      # True
```

The key difference here is that of precision: Floats can store up to 15-17 decimal points in precision. Here's a very strange situation as a consequence of this precision limitation:

```python
1.00000000000000001 == 1.0  # True
1.000001 == 1.0             # False
```

For the most part, unless you are doing scientific computing, this should really not matter.

{:.callout}

> ## A Note about numbers in Python 2.X
>
> Although the difference between integers and float is largely academic in Python 3, this is not the case in Python 2.X. This is because until Python 3, Python did not do a float conversion automatically when division is performed. This is important if you are still working in Python 2.7. In Python 2, you **must** do a type coercion when you perform division or Python will assume you want an integer result when you divide 2 integers.

# Mathematics in Python works like our everyday math

Some of the common operations - addition, subtraction, multiplication and division -- works the same as you will in Excel so we will not need to go through them explictly. We will only go through two operations that differ: exponentiation, and modulus. To raise a value to a certain power, we will use the `**` operator. Modulus simply tells us the remainder of a division. For instance:

```python
5 % 1
# Output: 1
```

One of the most common thing you will need to do is formatting your floats (i.e. returning your float in a specified number of decimal places). There are two ways to do this: using `round` or using `f-strings`. The snippets below show both approachs:

```python
LONG_FLOAT = 2.351645461231

# Using round:
rounded_float = round(LONG_FLOAT, 2)

# Using f-strings:
formatted_float = f"{LONG_FLOAT:.2f}"

print(rounded_float)  # Output: 2.35
print(formatted_float)  # Output: 2.35
```

The `f-string` method can further be used to format our float to have an equal width for the purposes of presentation. For instance:

```python
LONG_FLOAT = 2.351645461231
LONG_FLOAT2 = 12.351645461231

# To format both LONG_FLOAT to have the same width
formatted_float = f"{LONG_FLOAT:05.2f}"
formatted_float2 = f"{LONG_FLOAT2:5.2f}"
```

Note that the width will also include any decimals and spaces.

{:.callout}

> ## What if?
>
> What happens when you try to specify a padding is not sufficient to include both the whole number and the decimal? For instance, if we want a width of 4 for 12.3564?

{:.challenge}

> ## Try it
>
> Try to perform rounding of `pi`.
>
> ```python
> import math
> PI = math.pi
>
> # TODO: Fill in the blanks
>
> # Two methods to get PI up to 2 decimal places
> pi_two_decimals = ______(PI, _)
> pi_two_decimals = _"____"
>
> ```

# ⏰ Working with Dates and Times in Python

When you ask someone what today’s date is, they’ll probably just say something like “31 July 2025”. Simple, right?

But in Python (and in computing generally), dates and times are much trickier than they look. Why? Because what we casually call "date and time" is actually a lot of data packed together:

1. The year, month, and day (the calendar date)
2. The hour, minute, and second (the clock time)
3. The time zone (is this New York time or Tokyo time?)

Python doesn’t try to reinvent the wheel for this — instead, it gives us the powerful `datetime` module that makes handling dates and times much easier.

To work with dates and times, we will need to import the `datetime` module.

{:.challenge}

> ## Revision
>
> How do you import the date time module?

# Working with the datetime object

The `datetime` module provides a class called `datetime` that represents a specific point in time. You can create a `datetime` object like this:

```python
from datetime import datetime

now = datetime.now()
print (now)

# Output: datetime.datetime(2025, 8, 1, 15, 51, 40, 510770)
```

You will notice that when you print `now`, you will get what looks like a tuple. This contains a few pieces of information:

- The year (2025)
- The month (8 for August)
- The day (1)
- The hour (15, in 24-hour format)
- The minute (51)
- The second (40)
- The microsecond (510770)

Likewise, we can also create a new datetime as follows:

```python
from datetime import datetime
new_date = datetime(2025, 8, 1, 15, 51, 40)
print(new_date)
# Output: datetime.datetime(2025, 8, 1, 15,
# 51, 40)
```

You might be wondering why we might want to create a date time object? This is because we are able to do handy operations like find out how many days are there intervening. We will touch on some handy date-time operations next.

# Mathematics with dates

When working with dates in Python, one of the most powerful features is that you can do math with dates! Instead of manually counting days on a calendar, Python’s `datetime` module can tell you the exact difference between two dates.

For example, let’s say you’re counting down to your big trip to Korea:

```python
from datetime import datetime

VACATION_DATE = datetime(2025, 12, 25, 2, 00, 00)
TODAY = datetime(2025, 8,1)

# How many more days am I from going to Korea?
delta = VACATION_DATE - TODAY
print (delta)
# Output: datetime.timedelta(days=146, seconds=7200)
```

Unfortunately, that means you am 146 days away from my holiday to Korea T_T

Now, what if we want to convert from days into weeks and days? Unfortunately, the timedelta object only holds the time in days and microseconds. We can extract the these information as follows:

```python
total_seconds = delta.total_seconds()
print (total_seconds)
# Output: 12621600.0

total_days = delta.days
print (total_days)
# Output: 146
```

{:.challenge}

> ## Try it
>
> Try to calculate the total number of weeks, hours and minutes from today to your next big date!
>
> ```python
> from datetime import datetime
> now = datetime.now()
> ```

# Specifying the format of dates

When Python shows us a raw datetime object like

```python
datetime.datetime(2025, 8, 1, 15, 51, 40, 510770)
```

…it’s giving us the computer‑friendly version. But as humans, we don’t usually want to read dates this way.

So how do we tell Python, “Hey, show me this in a nice, human‑friendly format”?

This is done using … wait for it … string formatting! 🎉

The datetime module gives us a method called .strftime() (string format time), which lets us choose exactly how the date and time should appear.

For example:

```python
import datetime

now = datetime.datetime.now()

print(now.strftime("%Y-%m-%d %H:%M:%S")) # Output: 2025-08-01 15:51:40
print(now.strftime("%A, %B %d, %Y"))     # Output: Friday, August 01, 2025

```

{:.callout}

> ## 📌 Common strftime codes
>
> Here are some you’ll use all the time:
>
> | Code | Meaning                  | Example |
> | ---- | ------------------------ | ------- |
> | %Y   | Year (4 digits)          | 2025    |
> | %y   | Year (last 2 digits)     | 25      |
> | %m   | Month (2 digits)         | 08      |
> | %B   | Full month name          | August  |
> | %b   | Abbreviated month name   | Aug     |
> | %d   | Day of the month         | 01      |
> | %A   | Full weekday name        | Friday  |
> | %a   | Abbreviated weekday name | Fri     |
> | %H   | Hour (24‑hour clock)     | 15      |
> | %I   | Hour (12‑hour clock)     | 03      |
> | %p   | AM / PM                  | PM      |
> | %M   | Minutes                  | 51      |
> | %S   | Seconds                  | 40      |

👉 So with `.strftime()`, we can make Python say exactly what we want: whether it’s 2025-08-01, August 1, 2025, or even Fri 01/08/25 3:51 PM.

{:.challenge}

> ## Try it
>
> Try to perform the following date-time formatting
>
> ```python
> # TODO: Fill in the blanks
> from datetime import datetime
>
> now = datetime.now()
>
> # To get date in the dd/mm/yyyy format (e.g. 01/08/2025)
> now.strftime("__/__/__")
>
> # To get date in the dd-mmm-yyyy format (e.g. 01-Aug-2025)
> now.strftime("________")
>
> # To print the time in HH:MM format in 24 hours:
> now.______________
>
> # To print date/time in the 24 hour format (dd-mm-yyyy. HH:MM)
> now.______________
> ```

What if we have a string in a specific format and we want to convert that into a datetime object? This can be done in Python by us providing the string and the format in which the date is presently formatted in. For instance:

```python
from datetime import datetime

date_string = "2025-08-01"
date_object = datetime.strptime(date_string, "%Y-%m-%d")
print(date_object)  # Output: 2025-08-01 00:00
```

{:.challenge}

> ## Try it
>
> Now, lets apply what you have learned above to our API response. Our API response provided a timestamp in the JSON format. Create a datetime object from the datetime string provided at the end of the JSON response.
>
> ```python
> # TODO: Fill in the blanks
> import _______  # import library for querying API
> import _______  # import library for working with date and time
>
> URL = "https://api-open.data.gov.sg/v2/real-time/api/twenty-four-hr-forecast?date=2025-12-01"
> response = ____________________                      # Get the response from the API
> results = _________________                          # Get the results contained in the response body
> data = ________________                              # Get the data stored in the 'data' key
> timestamp = ___________                              # Get timestamp contained in the 'timestamp' key
> print (timestamp) # Output: 2025-01-01T05:30:00
> datetime_string = ___________[_]                     # Get everything before the + string
> datetime_object = datetime.________(_______________) # Convert the datetime string into a datetime object by specifying the format
> print (datetime_object)
> ```

{:.callout}

> ## FYI
>
> The timestamp provided (2025-01-01T05:30:00) from the API is in a format known as the **ISO 8601 formatted string**. This is a standardized way in which time can be shared across systems. Because this is such a commonly used standard, the `datetime` library provides a quick way to convert this into a `datetime` object. This is done as follows:
>
> ```python
> timestamp = "2025-01-01T05:30:00:"
> datetime.fromisoformat(timestamp)
> # Output: datetime.datetime(2025, 1, 1, 5, 30)
> ```

# Conclusion

In this section, we learned how to work with numeric data and time in Python. We explored the differences between integers and floats, performed basic arithmetic operations, and worked with dates and times using the `datetime` module.
