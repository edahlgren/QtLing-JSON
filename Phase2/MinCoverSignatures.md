---
layout: default
title: Filter for minimal cover
parent: Phase 2
nav_order: 4
---

# Filter for minimal cover

TODO: add description ...

+ [Input: signature quadruples](#input)
+ [Output: signature quadruples](#output)

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

See [Create signatures (output)](../Phase1/CreateSignatures.html#output) for more details.

---

# Output

## Input 1

A JSON formatted file containing a set of signature quadruples filtered for only those that satisfy a minimal cover condition.

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

This format is the same as the input.
