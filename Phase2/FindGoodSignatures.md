---
layout: default
title: Find good signatures
parent: Phase 2
nav_order: 5
---

# Find good signatures

TODO: add description ...

+ [Input 1: word list](#input-1)
+ [Input 2: protostems words](#input-2)
+ [Input 3: minimal cover signature quadruples](#input-3)
+ [Output: good signature quadruples](#output)

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

A mapping of protostems to start and end indexes in a word list.

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

See [Find protostem words (output)](./FindProtostemWords.html#output) for more details.

# Input 3

A JSON formatted file containing a set of signature quadruples filtered for only those that satisfy a minimal cover condition.

```
{
    "signatures": [
        {
            "sig": "[a-z]+",
            "stem": "[a-z]+",
            "affix": "[a-z]+",
            "word": "[a-z]+"
        },
        ...
    }
}
```

See [Create signatures (output)](../Phase1/CreateSignatures.html#output) for more details.

---

## Output

A JSON formatted file containing a set of "good" signature quadruples.

```
{
    "signatures": [
        {
            "sig": "[a-z]+",
            "stem": "[a-z]+",
            "affix": "[a-z]+",
            "word": "[a-z]+"
        },
        ...
    }
}
```

This format is the same as input 3.
