---
layout: default
title: Find protostems
parent: Phase 1
nav_order: 1
---

# Find protostems

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step1_from_words_to_protostems()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L76).

Substeps:

+ [Find protostem sets](#find-protostem-sets)
+ [Find protostem words](#find-protostem-words)

---

#### Find protostem sets

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is the first half of [CLexicon::step1_from_words_to_protostems()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L76).

This step iterates through a sorted word list and finds a set of "protostems" which will later be transformed into real stems.

+ [Input: a sorted word list](#input-11)
+ [Output: a set of protostems](#output-12)

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

#### Output 1.2

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

Each string in the "protostems" array is the name of a protostem.

---

#### Find protostem words

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is the [second half of CLexicon::step1_from_words_to_protostems()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L162).

This step finds the subset of words associated with a protostem and creates a mapping of protostems to words.

+ [Input: a sorted word list](#input-21)
+ [Input: a set of protostems](#input-22)
+ [Output: a map of protostems to words](#output-23)
  + [Example](#example-24)

---

#### Input 2.1

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

#### Input 2.2

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

See [Output 1.2](#output-12) for more details.

---

#### Output 2.3

---

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

#### Example 2.4

---

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
