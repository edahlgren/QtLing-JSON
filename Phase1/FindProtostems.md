---
layout: default
title: Find protostems
parent: Phase 1
nav_order: 1
---

# Find protostems

TODO: Add description

+ [Input](#input)
+ [Output](#output)

### Input

A JSON formatted file containing an array of lowercased sorted words and their frequencies.

```
{
    "words": [
        {
            "name": "[a-z]+"
            "count": [0-1]+,
        },
        ...
    ]
}
```

See Preprocessing (output) for more details.

### Output

A JSON formatted file containing the set of all protostems.

```
{
    "protostems": [
         "[a-z]+",
         ...
     ]
}
```

For each string in the "protostems" array:

+ The name of a protostem.
