---
layout: default
title: Create affix signatures
parent: Phase 1
nav_order: 5
---

# Create affix signatures

TODO: Add description

+ [Input](#input)
+ [Output](#output)

---

## Input

A JSON formatted file containing a mapping of stems to all affixes.

```
{
    "stems_to_affixes": [
        {
            "stem": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

See [Map stems (output)](./MapStems.html#output) for more details.

---

## Output

A JSON formatted file containing the set of signatures and their component affixes.

```
{
    "signatures": [
        {
            "full": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

For each JSON object in the "signatures" array:

+ A `"full"` field with a string value that is a full signature (affixes joined with `"="`).
+ A `"affixes"` field with an array value that is the set of affixes that make up the signature.
