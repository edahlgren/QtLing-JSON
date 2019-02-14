---
layout: default
title: Create presignatures
parent: Phase 1
nav_order: 5
---

# Create presignatures

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

A JSON formatted file containing a set of presignatures and their component affixes.

```
{
    "presignatures": [
        {
            "sig": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

For each JSON object in the "presignatures" array:

+ A `"sig"` field with a string value that is a presignature (affixes joined with `"="`).
+ A `"affixes"` field with an array value that is the set of affixes that make up the presignature.
