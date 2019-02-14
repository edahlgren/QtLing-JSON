---
layout: default
title: Sort good signature stems
parent: Phase 2
nav_order: 6
---

# Sort good signature stems

TODO: add description ...

+ [Input: good signature quadruples](#input)
+ [Output: mapping of signatures to stems](#output)

## Input

A JSON formatted file containing a set of "good" signature quadruples.

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

## Output

A JSON formatted file containing a mapping of signatures to a sorted list of stems.

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

See [Map signatures to stems](./MapSignaturesToStems.html#output) for more details.
