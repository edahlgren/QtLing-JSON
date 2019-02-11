---
layout: default
title: Find protostem words
parent: Phase 1
nav_order: 2
---

# Find protostem words

TODO: Add description

+ [Input 1](#input-1)
+ [Input 2](#input-2)
+ [Output](#output)

---

## Input 1

A JSON formatted file containing an array of lowercased sorted words and their frequencies.

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

See [Preprocessing (output)](../Preprocessing.html#output) for more details.

## Input 2

A JSON formatted file containing the set of all protostems.

```
{
    "protostems": [
         "[a-z]+",
         ...
     ]
}
```

See [Find protostems (output)](./FindProtostems.html#output) for more details.

---

## Output

A map of protostems to start and end indexes in a word list.

```
{
    "protostem_to_words": {
        "[a-z]+": {
            "word_end_index": [0-9]+,
            "word_start_index": [0-9]+
        },
        ... 
     },
     "wordlist": "/path/to/words.json"
}
```

For each field in the "protostem_to_words" object:

+ The field name is a protostem.
+ The value is a JSON object containing:
  + A `"word_start_index"` with a numeric value that is the start index in a word list.
  + A `"word_end_index"` with a numeric value that is the end index in a word list.

The `"wordlist"` points to a JSON file containing a word list.

---

#### Example

```
{
    "protostem_to_words": {
        "that": {
            "word_start_index": 6
            "word_end_index": 10,
        }
    },
    "wordlist": "/home/qtling/words.json"
}
```
