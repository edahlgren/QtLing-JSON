---
layout: default
title: Resignaturize
parent: Phase 2
nav_order: 1
---

# Resignaturize

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step6_ReSignaturizeWithKnownAffixes()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab2.cpp#L68).

Substeps:

+ [Map stems to affixes v2](#map-stems-to-affixes-v2)
+ [Create presignatures](#create-presignatures)
+ [Find signatures](#find-signatures)

---

#### Map stems to affixes v2

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step6a_create_temporary_stem_to_sig_map()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab2.cpp#L125).

This step rebuilds a mapping of stems to affix sets by checking the set of affixes produced by the [find signatures](../Phase1/FindSignatures.html) step.

+ [Input: a set of word parts](#input-11)
+ [Input: a list of sorted affixes](#input-12)
+ [Output: a map of stems to affixes](#output-13)

---

#### Input 1.1

---

A JSON formatted file containing the parts (stem, affix) of each word.

```
{
    "word_parts": [
        {
            "stem": "[a-z]+",
            "affix": "[a-z]+"
            "word": "[a-z]+"
        },
        ...
    }
}
```

See [Find word parts (Output 1.3)](../Phase1/FindWordParts.html#output-13) for more details.

---

#### Input 1.2

---

A JSON formatted file containing a list of affixes sorted by their frequency in a set of signatures.

```
{
    "affixes": [
        {
            "affix": "[a-z]+"
            "count": [0-9]+,
        },
        ...
    ]
}
```

See [FindSignatures (Output 2.2)](../Phase1/FindSignatures.html#output-22) for more details.

---

#### Output 1.3

---

A JSON formatted file containing a mapping of stems to affixes.

```
{
    "stems_to_affixes": [
        {
            "stem": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

See [Find presignatures (Output 1.2)](../Phase1/FindPresignatures.html#output-12) for more details.

---

#### Create presignatures

---

Redo [Create presignatures](../Phase1/FindPresignatures.html#create-presignatures) from Phase 1.

---

#### Find signatures

---

Redo [Find signatures](../Phase1/FindSignatures.html) from Phase 1.
