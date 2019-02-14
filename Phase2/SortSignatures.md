---
layout: default
title: Sort signatures
parent: Phase 2
nav_order: 3
---

# Sort signatures

TODO: add description ...

+ [Input 1: signature quadruples](#input-1)
+ [Input 2: sorted affixes](#input-2)
+ [Output: sorted signature quadruples](#output)

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

See [Create signatures (output)](../Phase1/CreateSignatures.html#output) for more details.

## Input 2

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

See [Sort affixes (output)](../Phase1/SortAffixes#output) for more details.

## Output

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

This format is the same as input 1.
