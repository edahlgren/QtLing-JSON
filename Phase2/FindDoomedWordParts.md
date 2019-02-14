---
layout: default
title: Find doomed word parts
parent: Phase 2
nav_order: 11
---

# Find doomed word parts

TODO: add description

+ [Input 1: signature quadruples](#input-1)
+ [Input 2:: doomed signatures](#input-2)
+ [Output: word parts](#output)

---

## Input 1

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

See [Create signatures (output)](./CreateSignatures.html#output) for more details.


## Input 2

A JSON formatted file containing "doomed" signatures and "doomed" affixes.

```
{
    "doomed_signatures": {
        "[a-z]+": {
            "edgeId": [0-9]+,
            "doomed_affixes": [
                "[a-z]+",
                ...
            ]
        },
        ...
    }
    "edges": /path/to/complex_edges.json
}
```

See [Find doomed signatures (output)](./FindDoomedSignatures.html#output)

---

## Output

A JSON formatted file containing a mapping of words to signature triples.

```
{
    "words_to_triples": {
        "[a-z]+": [
            {
                "signature": "[a-z]+",
                "stem": "[a-z]+",
                "affix": "[a-z]+"
            },
            ...
        ],
        ...
    }
}
```

See [Map words to signature triples (output)](../Phase1/MapWordsToSignatureTriples.html#output) for more details.
