---
layout: default
title: Find word parts
parent: Phase 1
nav_order: 3
---

# Find word parts

TODO: Add description

+ [Input 1](#input-1)
+ [Input 2](#input-1)
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

A JSON formatted file containing the parts (stem, affix) of each word.

```
{
    "word_parts": [
        {
            "stem": "[a-z]+",
            "affix": "[a-z]+",
            "word": "[a-z]+"
        },
        ...
    }
}
```

For each JSON object in the "word_parts" array:

+ A `"stem"` field with a string value that is the word stem.
+ An `"affix"` field with a string value that is the word affix (prefix or suffix).
+ A `"word"` field with the full word. Can be omitted.
