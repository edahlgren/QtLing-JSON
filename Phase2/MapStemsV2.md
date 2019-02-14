---
layout: default
title: Map stems v2
parent: Phase 2
nav_order: 1
---

# Map stems v2

This is [step6a_create_temporary_stem_to_sig_map()]() ...

+ [Input 1: word parts](#input-1)
+ [Input 2: sorted affixes](#input-2)
+ [Output: mapping of stems to affixes](#output)

---

## Input 1

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

See [Find word parts (output)](../Phase1/FindWordParts.html#output) for more details.

## Input 2

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

See [Sort affixes (output)](../Phase1/SortAffixes#output) for more details.

---

# Output

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

See [Map stems (Phase 1)](../Phase1/MapStems.html#output) for more details.
