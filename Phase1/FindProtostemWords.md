---
layout: default
title: Find protostem words
parent: Phase 1
nav_order: 2
---

# Find protostem words

TODO: Add description

+ [Input](#input)
+ [Output](#output)

### Input

A JSON formatted file containing the set of all protostems.

```
{
    "protostems": [
         "[a-z]+",
         ...
     ]
}
```

See Find protostems (output) for more details.

### Output

A map of protostems to start and end indexes in a word list.

```
{
    "protostem_to_words": {
        [a-z]+: {
            "word_end_index": [0-9]+,
            "word_start_index": [0-9]+
        },
        ... 
     },
     "wordlist": "/path/to/words.json"
}
```

For each field in the "protostem_to_words" object:

+ The field name is a protostem string.
+ The value is a JSON object containing:
  + A `"word_start_index"` with a numeric value that is the start index in a word list.
  + A `"word_end_index"` with a numeric value that is the end index in a word list.

The `"wordlist"` points to a JSON file containing a word list.

For example:

```
{
    "protostem_to_words": {
        "that": {
            "word_start_index": 6
            "word_end_index": 10,
    },
    "wordlist": "/home/qtling/words.json"
}
```
