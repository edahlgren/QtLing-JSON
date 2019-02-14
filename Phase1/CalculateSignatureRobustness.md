---
layout: default
title: Calculate robustness
parent: Phase 1
nav_order: 9
---

# Calculate robustness

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CSignatureCollection::calculate_sig_robustness()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/SignatureCollection.cpp#L291).

This step calculates a measure of signature robustness based on maps of signatures to stems and affixes. The result is a map of signatures to a robustness score.

+ [Input: a map of signatures to stems](#input-11)
+ [Input: a map of signatures to affixes](#input-12)
+ [Output: a map of signatures to robustness](#output-13)

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

#### Input 1.2

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

#### Output 1.3

---

A JSON formatted file containing a mapping of signatures to robustness.

```
{
    "signature_robustness": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

For each field in the "signature_robustness" JSON object:

+ The field name is a signature.
+ The value is the signature's robustness.
