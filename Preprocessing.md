---
layout: default
title: Preprocessing
nav_order: 3
---

# Preprocessing

TODO: Add description

+ [Input](#input)
+ [Output](#output)

### Input

A [DX1]() formatted file containing line-separated words in a lexicon, where words and their frequencies are separated by spaces.

```
[A-Za-z]+ [0-9]+ [A-Za-z]+ ... [A-Za-z]+
```

For each line:

+ First token (word) is required
+ Second token (word frequency) is optional
+ All other tokens are ignored.

For example:

```
the 63146 t h e
of 36022 o f
and 27624 a n d
to 25647 t o
a 21970 a
in 19451 i n
that 9940 t h a t
is 9775 i s
was 9625 w a s
for 8817 f o r
```

### Output

A JSON formatted file containing an array of lowercased sorted words and their frequencies. See [Finding suffixes]() and [Finding prefixes]() for details on sorting.

```
{
    "words": [
        {
            "name": "[a-z]+"
            "count": [0-1]+,
        },
        ...
    ]
}
```

For each JSON object in the "words" array:

+ A `"name"` field with a string value that is the lowercased word. Should not be empty.
+ A `"count"` field with a numeric value that is the frequency of the word. Defaults to 1.

> **NOTE:** A `typename` field is optional but recommended. See the RFC for more details.

#### Finding suffixes

To find suffixes, words must be ordered lexigraphically.

For example:

```
{
    "words": [
        {
            "name": "a",
            "count": 21970
        },
        {
            "name": "and",
            "count": 27624
        },
        {
            "name": "for",
            "count": 8817
        },
        {
            "name": "in",
            "count": 19451
        },
        {
            "name": "is",
            "count": 9775
        },
        {
            "name": "of",
            "count": 36022
        },
        {
            "name": "that",
            "count": 9940
        },
        {
            "name": "the",
            "count": 63146
        },
        {
            "name": "to",
            "count": 25647
        },
        {
            "name": "was",
            "count": 9625
        }
    ]
}
```

#### Finding prefixes

To find prefixes, words must be ordered lexigraphically when they are reversed.

For example:

```
{
    "words": [
        {
            "name": "a",
            "count": 21970
        },
        {
            "name": "and",
            "count": 27624
        },
        {
            "name": "the",
            "count": 63146
        },
        {
            "name": "of",
            "count": 36022
        },
        {
            "name": "in",
            "count": 19451
        },
        {
            "name": "to",
            "count": 25647
        },
        {
            "name": "for",
            "count": 8817
        },
        {
            "name": "was",
            "count": 9625
        },
        {
            "name": "is",
            "count": 9775
        },
        {
            "name": "that",
            "count": 9940
        }
    ]
}
```
