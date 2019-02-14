---
layout: default
title: Map stems
parent: Phase 1
nav_order: 4
---

# Map stems

TODO: Add description

+ [Input](#input)
+ [Output](#output)

---

## Input

A JSON formatted file containing the parts (stem, affix) of each word.

```
{
    "word_parts": [
        {
            "stem": "[a-z]+",
            "affix": "[a-z]+"
            "word": "[a-z]+"
        },
        ...
    }
}
```

See [Find word parts (output)](./FindWordParts.html#output) for more details.

---

## Output

A JSON formatted file containing a mapping of stems to affixes.

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

For each JSON object in the "stems_to_affixes" array:

+ A `"stem"` field with a string value that is a word stem.
+ An `"affixes"` field with an array value that is the set of affixes that the stem (above) is found with.
