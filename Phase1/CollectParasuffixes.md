---
layout: default
title: Collect parasuffixes
parent: Phase 1
nav_order: 8
---

# Collect parasuffixes

TODO: Add description

+ [Input A: mapping of signatures to stems](#input-A)
+ [Output A: signatures with a single stem](#output-A)

+ [Input B: signatures with a single stem](#input-B)
+ [Output B: sorted affixes](#output-b)

---

## Input A

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

See [Map signatures to stems](./MapSignaturesToStems.html#output) for more details.

---

## Output A

A JSON formatted file containing a mapping of signatures to a single stem.

```
{
    "single_stem_signatures": {
        "[a-z]+": [ "[a-z]+" ],
        ...
    }
}
```

This format is the same as the input for compatibility with other steps.

---

## Input B

A JSON formatted file containing a mapping of signatures to a single stem.

```
{
    "single_stem_signatures": {
        "[a-z]+": [ "[a-z]+" ],
        ...
    }
}
```

See above.

---

## Output B

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

See [Sort affixes (output)](./SortAffixes.html#output) for more details.
