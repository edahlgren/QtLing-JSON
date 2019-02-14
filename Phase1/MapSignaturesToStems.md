---
layout: default
title: Map signatures to stems
parent: Create signature quadruples
nav_order: 4
---

# Map signatures to stems

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

---

## Output

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

For each field in the "signatures_to_stems" JSON object:

+ The field name is a signature.
+ The value is a list of stems associated with the signature.
