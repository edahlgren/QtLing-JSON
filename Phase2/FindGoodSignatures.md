---
layout: default
title: Find good signatures
parent: Phase 2
nav_order: 2
---

# Find good signatures

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step7_FindGoodSignaturesInsideParaSignatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab2.cpp#L177).

Substeps:

+ [Sort signatures](#sort-signatures)
+ [Find minimal cover](#find-minimal-cover)
+ [Create good signatures](#create-good-signatures)
+ [Sort good signature stems](#sort-good-signatures)

---

#### Sort signatures

---

Redo [Sort signatures](../Phase1/FindContainmentLists.html#sort-signatures) from Phase 1.

---

#### Find minimal cover

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CSignatureCollection::find_minimal_cover()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L236).

This step isolates signatures that satisfy a "minimal cover" condition.

+ [Input: a set of signature quadruples](#input-11)
+ [Output: a set of signature quadruples](#output-12)

---

#### Input 1.1

---

A JSON formatted file containing a set of signature quadruples.

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

See [Find signatures (Output 1.3)](../Phase1/FindSignatures.html#output-13) for more details.

---

#### Output 1.2

---

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

This format is the same as [Input 1.1](#input-11).

---

#### Create good signatures

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is main for-loop of [CLexicon::step7_FindGoodSignaturesInsideParaSignatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab2.cpp#L177).

This step iterates over a mapping of protostems to words and constructs a set of "good" signatures. The result is a set of signature quadruples.

+ [Input: a sorted word list](#input-21)
+ [Input: a map of protostems to words](#input-22)
+ [Input: a set of minimal cover signature quadruples](#input-23)
+ [Output: a set of good signature quadruples](#output-24)

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

See [Find protostems (Output 2.3)](../Phase1/FindProtostems.html#output-23) for more details.

---

#### Input 2.3

---

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

See [Find signatures (Output 1.3)](../Phase1/FindSignatures.html#output-13) for more details.

---

#### Output 2.4

---

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

This format is the same as [Input 2.3](#input-23).

---

#### Sort good signature stems

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CSignatureCollection::sort_each_signatures_stems_alphabetically()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L169).

This step sorts the stems associated with a signature alphabetically. The result is a mapping of signatures to sorted stems.

+ [Input: a set of good signature quadruples](#input-31)
+ [Output: a map of signatures to stems](#output-32)

---

#### Input 3.1

---

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

See [Find signatures (Output 1.3)](../Phase1/FindSignatures.html#output-13) for more details.

---

#### Output 3.2

---

A JSON formatted file containing a mapping of signatures to a sorted list of stems.

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

See [Find signatures (Output 5.2)](../Phase1/FindSignatures.html#output-52) for more details.
