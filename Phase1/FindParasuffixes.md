---
layout: default
title: Find parasuffixes
parent: Phase 1
nav_order: 7
---

# Find parasuffixes

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::collect_parasuffixes()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L993).

Substeps:

+ [Find parasignatures](#find-parasignatures)
+ [Generate parasuffixes](#generate-parasuffixes)

---

#### Find parasignatures

---

This step filters a mapping of signatures to stems for "parasignatures", which are signatures with only a single stem.

+ [Input: a map of signatures to stems](#input-11)
+ [Output: a map of signatures to a single stem](#output-12)

---

#### Input 1.1

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

#### Output 1.2

---

A JSON formatted file containing a mapping of signatures to a single stem.

```
{
    "signatures_to_stems": {
        "[a-z]+": [ "[a-z]+" ],
        ...
    }
}
```

This format is the same as the input for compatibility with other steps.

---

#### Generate parasuffixes

---

This step collects and sorts the affixes of parasignatures by their frequency in all parasignatures.

+ [Input: a set of signatures with a single stem](#input-21)
+ [Output: a sorted list of parasuffixes](#output-22)

---

#### Input 2.1

---

A JSON formatted file containing a mapping of signatures to a single stem.

```
{
    "single_stem_signatures": {
        "[a-z]+": [ "[a-z]+" ],
        ...
    }
}
```

See [Output 1.2](#output-12) for more details.

---

#### Output 2.2

---

A JSON formatted file containing a list of parasuffixes sorted by their frequency in a set of signatures.

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

See [Find signatures (Output 2.2)](./FindSignatures.html#output-22) for more details.
