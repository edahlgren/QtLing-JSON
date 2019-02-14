---
layout: default
title: Calculate signature robustness
parent: Phase 1
nav_order: 12
---

# Calculate signature robustness

TODO: Add description

+ [Input 1: mapping of signatures to stems](#input-1)
+ [Input 2: mapping of signatures to affixes](#input-2)
+ [Output: mapping of signatures to robustness](#output)

---

## Input 1

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

## Input 2

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

See [Map signatures to affixes (output)](../MapSignaturesToAffixes.html#output) for more details.

---

## Output

A JSON formatted file containing a mapping of signatures to robustness.

```
{
    "signature_robustness": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

For each field in the "signature_robustness" JSON object:

+ The field name is a signature.
+ The value is the signature's robustness.
