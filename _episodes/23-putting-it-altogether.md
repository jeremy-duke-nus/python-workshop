---
title: Putting it altogether
teaching: 10
exercises: 60
questions:
  - Are you ready to write your first Python code to work with the API of your choice?
objectives:
  - Apply the concepts covered over the last two days to process data from an API of your choice.
keypoints:
  - Python programming is not that hard!
---

# Task Description

In this section, we will be using data from the [data.gov.sg](data.gov.sg), which is an open data portal provided by the Singapore government. In it, you can download data from a wide-range of categories such as education, housing and health. For today's exercise, we will be using the NEA endpoint that will provide us rainfall data. The API endpoint is as follows: `"https://api-open.data.gov.sg/v2/real-time/api/rainfall"`

The API endpoint returns something like this:

```python
{
  "code": 1,
  "errorMsg": null,
  "data": {
    "stations": [
      {
        "id": "S111",
        "deviceId": "S111",
        "name": "Scotts Road",
        "labelLocation": {
          "latitude": 1.31055,
          "longitude": 103.8365
        }
      }
    ],
    "readings": [
      {
        "timestamp": "2024-07-17T14:00:00.000Z",
        "data": [
          {
            "stationId": "S111",
            "value": 2
          }
        ]
      }
    ],
    "readingType": "TB1 Rainfall 5 Minute Total F",
    "readingUnit": "mm",
    "paginationToken": "b2Zmc2V0PTEwMA== (you will see this token only if next page exists)"
  }
}
```

Your challenge is to create a CSV file that looks like this:

```
location,latitude,longtitude,readings
Scotts Road,1.31055,103.8365,2
```

{:.callout}

> ## High Level Steps
>
> At a very high level, here's what you will need to do:
>
> 1. Get the response from the API (Hint: This is done using `requests`
> 2. Convert the response to a JSON (Hint: We can do this using `json()`) for easier manipulation
> 3. Extract the data from the body (Hint: This is found in `data`)
> 4. Create two empty dictionaries - one holding the coordinates, and one holding the reading
> 5. Using a loop, populate each dictionary with a key-value pair. Decide your key wisely! (Hint: `id` is common in both data sources)
> 6. Create a new file (Hint: You will need to use the `w` mode in `open`)
> 7. Loop through the keys of either one of the two dictionaries, then using the key, look up the corresponding information in the other dictionary.
> 8. Write the line out into the file (Hint: Use `f`-strings and `write`)
