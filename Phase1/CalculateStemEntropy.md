---
layout: default
title: Calculate stem entropy
parent: Phase 1
nav_order: 5
---

# Calculate stem entropy

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CSignatureCollection::calculate_stem_entropy()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L192). It is called by [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405) on a set of newly created signatures.

This step iterates through a mapping of signatures to stems and calculates the "stem entropy" of each signature. The result is a mapping of signatures to stem entropy.

+ [Input: a map of signatures to stems](#input-11)
+ [Output: a map of signatures to stem entropy](#output-12)

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

A JSON formatted file containing a mapping of signatures to stem entropy.

```
{
    "stem_entropy": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

For each field in the "stem_entropy" JSON object:

+ The field name is a signature.
+ The value is the signature's stem entropy.
