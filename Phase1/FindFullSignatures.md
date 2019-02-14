---
layout: default
title: Find full signatures
parent: Phase 1
nav_order: 13
---

# Find full signatures

This skips [step5a_replace_parse_pairs_from_current_signature_structure()]() ...

+ [Input 1: word list](#input-1)
+ [Input 2: map of signatures to stem entropy](#input-2)
+ [Input 3: map of signatures to stems](#input-3)
+ [Input 4: map of signatures to affixes](#input-4)
+ [Output 1: word parts](#output-1)
+ [Output 2: map of protostems to words](#output-1)

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

A JSON formatted file containing a mapping of signatures to stem entropy.

```
{
    "stem_entropy": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

See [Calculate stem entropy](./CalculateStemEntropy.html#output) for more details.

## Input 3

A JSON formatted file containing a mapping of signatures to the set of associated stems.

```
{
    "signatures_to_stems": {
        "[a-z]+": [
            "[a-z]+",
            ...
        ],
        ...
    }
}
```

See [Map signatures to stems](./MapSignaturesToStems.html#output) for more details.

## Input 4

A JSON formatted file containing a mapping of signatures to the set of associated affixes.

```
{
    "signatures_to_affixes": {
        "[a-z]+": [
            "[a-z]+",
            ...
        ],
        ...
    }
}
```

See [Map signatures to affixes](./MapSignaturesToAffixes.html#output) for more details.

---

## Output 1

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

See [Find word parts (output)](./FindWordsParts.html#output) for more details.

## Output 2

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
