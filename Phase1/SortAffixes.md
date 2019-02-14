---
layout: default
title: Sort affixes
parent: Phase 1
nav_order: 5
---

# Sort affixes

TODO: Add description

+ [Input: signature quadruples](#input)
+ [Output: sorted affixes](#output)

---

## Input

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

See [Create signatures (output)](../CreateSignatures.html#output) for more details.

## Output

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

For each JSON object in the "affixes" array:

+ An `"affix"` field with a string value that is an affix (prefix or suffix).
+ A `"count"` field with a number value that is the frequency of the affix in a set of signatures.
