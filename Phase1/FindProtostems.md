---
layout: default
title: Find protostems
parent: Phase 1
nav_order: 1
---

# Find protostems

This is the first half of [step1_from_words_to_protostems()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L76).

+ [Input: word list](#input)
+ [Output: protostems](#output)

---

## Input

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

---

## Output

A JSON formatted file containing the set of all protostems.

```
{
    "protostems": [
         "[a-z]+",
         ...
     ]
}
```

Each string in the "protostems" array is the name of a protostem.
