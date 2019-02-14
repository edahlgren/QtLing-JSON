---
layout: default
title: Find word parts
parent: Phase 1
nav_order: 2
---

# Find word parts

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step2_from_protostems_to_parses()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L222). There are no substeps.

This step finds stem and affix pairs ("word parts" or "parses") from words. The result is a set of triples where each triple contains a stem, affix, and word.

+ [Input: a sorted word list](#input-11)
+ [Input: a set of protostems](#input-12)
+ [Output: a set of word parts ("parses")](#output-13)

---

#### Input 1.1

---

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

See [Preprocessing (Output 1.2)](../Preprocessing.html#output-12) for more details.

---

#### Input 1.2

---

A JSON formatted file containing the set of all protostems.

```
{
    "protostems": [
         "[a-z]+",
         ...
     ]
}
```

See [Find protostems (Output 1.2)](./FindProtostems.html#output-12) for more details.

---

#### Output 1.3

---

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
+ A `"word"` field with the full word. Optional.
