---
layout: default
title: Find full signatures
parent: Phase 1
nav_order: 6
---

# Find full signatures

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step5b_find_full_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L737).

Substeps:

+ [Prepare for full signatures](#prepare-for-full-signatures)
+ [Find presignatures](#find-presignatures)
+ [Find signatures](#find-signatures)

---

#### Prepare for full signatures

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is the body of [CLexicon::step5b_find_full_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L737) before [CLexicon::step3_from_parses_to_stem_to_sig_maps()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L295).

This version skips [CLexicon::step5a_replace_parse_pairs_from_current_signature_structure()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L691) because the word parts can be trivially derived from the inputs to this step.

This step finds new word parts and a new mapping of protostems to words to prepare to find full signatures. The new word parts and the new mapping of protostems to words are passed to the next two steps which actually generate the new signature quadruples.

+ [Input: a word list](#input-11)
+ [Input: a map of signatures to stems](#input-12)
+ [Input: a map of signatures to affixes](#input-13)
+ [Input: a map of signatures to stem entropy](#input-14)
+ [Output: a set of word parts](#output-15)
+ [Output: a map of protostems to words](#output-16)

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

See [Find signatures (Output 5.2)](./FindSignatures.html#output-52) for more details.

---

#### Input 1.3

---

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

See [Find signatures (Output 4.2)](./FindSignatures.html#output-42) for more details.

---

#### Input 1.4

---

A JSON formatted file containing a mapping of signatures to stem entropy.

```
{
    "stem_entropy": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

See [Calculate stem entropy (Output 1.2)](./CalculateStemEntropy.html#output-12) for more details.

---

#### Output 1.5

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

See [Find word parts (Output 1.3)](./FindWordParts.html#output-13) for more details.

---

#### Output 1.6

---

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

See [Find protostems (Output 2.3)](./FindProtostems.html#output-23) for more details.

---

#### Find presignatures

---

Redo [Find presignatures](./FindPresignatures.html).

---

#### Find signatures

---

Redo [Find signatures](./FindSignatures.html).
