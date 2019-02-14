---
layout: default
title: Map signatures to affixes
parent: Create signature quadruples
nav_order: 3
---

# Map signatures to affixes

TODO: Add description

+ [Input: signature quadruples](#input)
+ [Output: mapping of signatures to stems](#output)

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

For each field in the "signatures_to_affixes" object:

+ The field name is a signature.
+ The value is a list of affixes associated with the signature.
