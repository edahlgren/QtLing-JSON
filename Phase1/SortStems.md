---
layout: default
title: Sort stems
parent: Phase 1
nav_order: 5
---

# Sort stems

TODO: Add description

+ [Input: signature quadruples](#input)
+ [Output: sorted stems](#output)

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

A JSON formatted file containing a list of stems sorted by their frequency in a set of words associated with signatures.

```
{
    "stems": [
        {
            "stem": "[a-z]+"
            "count": [0-9]+,
        },
        ...
    ]
}
```

For each JSON object in the "stems" array:

+ An `"stems"` field with a string value that is a stem.
+ A `"count"` field with a number value that is the frequency of the stem in a set of words associated with signatures.
