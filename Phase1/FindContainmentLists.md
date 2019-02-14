---
layout: default
title: Find containment lists
has_children: true
parent: Phase 1
nav_order: 8
---

# Find containment lists

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CSignatureCollection::compute_containment_list()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L151).

Substeps:

+ [Sort signatures](#sort-signatures)
+ [Compute containment lists](#compute-containment-lists)

---

#### Sort signatures

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CSignatureCollection::sort(SIG_BY_AFFIX_COUNT)](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L116).

This step sorts signature quadruples by affix count. The second input is optional because affix lists can trivially be derived from the signatures themselves and affixes can be recounted on the fly.

+ [Input: a set of signature quadruples](#input-11)
+ [Input: a sorted list of affixes](#input-12)
+ [Output: a sorted list of signature quadruples](#output-13)

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

See [Find signatures (Output 1.3)](./FindSignatures.html#output-13) for more details.

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

See [Find signatures (Output 2.2)](./FindSignatures.html#output-22) for more details.

---

#### Output 1.3

---

A JSON formatted file containing a set of signature quadruples sorted by affix count.

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

#### Compute containment lists

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is bulk of [CSignatureCollection::compute_containment_list()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L151).

This step computes a mapping of signatures to containment lists of signatures based on the number of affixes in a signature. The second input is optional because affix count can trivially be derived from the signatures themselves by splitting on the `"="` character.

+ [Input: a sorted list signature quadruples](#input-21)
+ [Input: a map of signatures to affixes](#input-22)
+ [Output: a map of signatures to containment lists](#output-23)

---

#### Input 2.1

---

A JSON formatted file containing a set of signature quadruples sorted by affix count.

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

See [Find signatures (Output 1.3)](./FindSignatures.html#output-13) for more details.

---

#### Input 2.2

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

#### Output 2.3

---

A JSON formatted file containing a mapping of signatures to containment lists.

```
{
    "containment_lists": {
        "[a-z]+": [
            "[a-z]+",
            ...
        ],
        ...
    }
}
```

For each field in the `"containment_lists` object:

+ The field is a signature.
+ The value is an array of signatures (a containment list).
