---
layout: default
title: Preprocessing
nav_order: 3
---

# Preprocessing

In QtLing this is [MainWindow::read_dx1_file()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/mainwindow.cpp#L610).

This step reads a lexicon from a file and sort words in the lexicon to prepare for finding either suffixes or prefixes.

+ [Input: set of words and frequencies](#input)
+ [Output: sorted word list](#output)

---

## Input

A [DX1](https://github.com/markandrus/DX1/blob/master/README.md) formatted file containing a lexicon. For each line, the first token is a word (required), the second token is the word frequency (optional), and all other tokens are ignored. Tokens must be space-separated.

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

---

## Output

A JSON formatted file containing an array of lowercased sorted words and their frequencies.

To find suffixes, words must be ordered lexigraphically. To find prefixes, words must be ordered lexigraphically when they are reversed.

```
{
    "words": [
        {
            "name": "[a-z]+"
            "count": [0-9]+,
        },
        ...
    ]
}
```

For each JSON object in the "words" array:

+ A `"name"` field with a string value that is the lowercased word.
+ A `"count"` field with a numeric value that is the frequency of the word. Should default to 1.

---

#### Example

For finding suffixes:

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

For finding prefixes:

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
