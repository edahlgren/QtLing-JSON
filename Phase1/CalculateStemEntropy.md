---
layout: default
title: Calculate stem entropy
parent: Phase 1
nav_order: 7
---

# Calculate stem entropy

TODO: Add description

+ [Input: mapping of signatures to stems](#input)
+ [Output: mapping of signatures to stem entropy](#output)

---

## Input

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

See [Map signatures to stems (output)](../MapSignaturesToStems.html#output) for more details.

---


## Output

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
