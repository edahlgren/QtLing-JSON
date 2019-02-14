---
layout: default
title: Find presignatures
parent: Phase 1
nav_order: 3
---

# Find presignatures

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step3_from_parses_to_stem_to_sig_maps()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L295).

Substeps:

+ [Map stems to affix lists](#map-stems-to-affix-lists)
+ [Create presignatures](#create-presignatures)

---

#### Map stems to affix lists

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step3a_from_parses_to_stem_to_sig_map()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L329).

This step creates a mapping of stems to affix sets based on a set of word parts.

+ [Input: a set of word parts](#input-11)
+ [Output: a map of stems to affix lists](#output-12)

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

See [Find word parts (Output 1.3)](./FindWordParts.html#output-13) for more details.

---

#### Output 1.2

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

For each JSON object in the "stems_to_affixes" array:

+ A `"stem"` field with a string value that is a word stem.
+ An `"affixes"` field with an array value that is the set of affixes that the stem (above) is found with.

---

#### Create presignatures

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step3b_from_stem_to_sig_map_to_sig_to_stem_map()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L355).

This step uses a mapping of stems to affix sets to create "presignatures". A presignature is a signature string and a set of component affixes. A presignature is a temporary structure used later to create full signatures.

+ [Input: a map of stems to affix sets](#input-21)
+ [Output: a set of presignatures](#output-22)

---

#### Input 2.1

---

A JSON formatted file containing a mapping of stems to all affixes.

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

See [Output 1.2](#output-12) for more details.

---

#### Output 2.2

---

A JSON formatted file containing a set of presignatures and their component affixes.

```
{
    "presignatures": [
        {
            "sig": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

For each JSON object in the "presignatures" array:

+ A `"sig"` field with a string value that is a presignature (affixes joined with `"="`).
+ An `"affixes"` field with an array value that is the set of affixes that make up the presignature.
