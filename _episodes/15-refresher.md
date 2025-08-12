---
title: Taking a jog down memory lane
teaching: 10
exercises: 30
questions:
  - What are we trying to do by the end of the session?
  - What have we covered in the session yesterday?
objectives:
  - Recap key concepts covered in Day 1
keypoints:
  - Variables are pieces of data held in memory.
  - Different data types behave differently; Python does not care about the correctness of your output, only the correctness of your input.
  - Conditional evaluation provides a tool for us to control program flow.
start: true
---

# 📢 Welcome Back to Day 2!

I hope everything we talked about yesterday is still relatively fresh in your minds. If not, fret not, we will start off the day with some hands-on refresher exercises.
As a reminder, we explored yesterday:

1. How data zips across the internet (like tiny digital postcards) and lands in our programs.
2. How to fetch an API response and read it without panicking at all those curly braces and square brackets.
3. How to work with different data types—text, numbers, and dates—so we can actually use that data.
4. How to make decisions in code using conditional logic (`if`, `elif`, `else`).

The things we covered yesterday will provide us the building blocks to write your very first program to process data from an API. Today, we’ll level up with:

1. Writing our own functions so our code can reuse its best tricks.
2. Loops to repeat actions without typing the same thing a hundred times.
3. Error handling so our programs don’t crash like a toddler on roller skates.
4. Reading from and writing to files so our work can be saved and shared.

And at the end of the day, you’ll get to pick an API of your choice and process its data like a pro!

# But first, refresher time!

Before we dive in to the contents for today, lets get everyone warmed up as we take a jog down memory lane. We will work in the same `conda` environment as we did yesterday for the workshop today, so you should not create a new environment. As a reminder, you can activate your environment by using the `conda activate <environment name>` command in your terminal.

## 1️⃣ Fetching and Reading API Data

Use the Open-Meteo API to get the current temperature for your city.
Print the temperature in a friendly sentence, e.g.,
"The current temperature in London is 22°C."
Hint: You’ll need the `requests` library.

## 2️⃣ Working with Data Types

Create variables for:
Your first name (string)
Your age (integer)
Today’s date (string in YYYY-MM-DD format)
Print each variable along with its data type (use type()).

## 3️⃣ Conditional Logic

Write a program that checks if today’s temperature (from exercise 1) is:
Above 25°C → print "It's a hot day!"
Between 15°C and 25°C → print "It's a pleasant day."
Below 15°C → print "Brrr, it's chilly."

## 4️⃣ Bonus Challenge

Use an API of your choice (e.g., PokéAPI, The Cat API, SpaceX API) to fetch some data, and print one fun fact about it.
