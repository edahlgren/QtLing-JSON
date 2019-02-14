---
layout: default
title: Generate hypotheses
parent: Phase 2
nav_order: 14
---

# Generate hypotheses

TODO: add description

+ [Input 1: complex graph edges](#input-1)
+ [Input 2: doomed signatures](#input-2)
+ [Output: hypotheses](#output)

---

## Input 1

A JSON formatted file containing a list of complex graph edges.

```
{
    "complex_edges": [
        {
            "signature1": "[a-z]+",
            "signature2": "[a-z]+",
            "morph": "[a-z]+",
            "word": "[a-z]+",
            "stems": [
                {
                    "word": "[a-z]+",
                    "stem1": "[a-z]+",
                    "stem2": "[a-z]+"
                }
            ]
        },
        ...
    ]
}    
```

See [Create complex edges (output)](./CreateComplexEdges.html#output) for more details.

## Input 2

A JSON formatted file containing "doomed" signatures and "doomed" affixes.

```
{
    "doomed_signatures": {
        "[a-z]+": {
            "edgeId": [0-9]+,
            "doomed_affixes": [
                "[a-z]+",
                ...
            ]
        },
        ...
    }
    "edges": /path/to/complex_edges.json
}
```

See [Find doomed signatures (output)](./FindDoomedSignatures.html#output)

---

## Output

A JSON formatted file containing "hypotheses" structures.

```
{
    "hypotheses": [
        {
            "signature1": "[a-z]+",
            "signature2": "[a-z]+",
            "new_signature": "[a-z]+",
            "morph": "[a-z]+",
            "new_edge: {
                "morph": "[a-z]+",
                "signature": "[a-z]+
            },
            "num_words": [0-9]+
        }
    ]
}
```

For each JSON object in the "hypotheses" array:

+ A `"signature1"` with a string value.
+ A `"signature2"` with a string value.
+ A `"new_signature"` with a string value.
+ A `"morph"` with a string value.
+ A `"new_edge"` with an object containing:
  + A `"morph"` with a string value.
  + A `"signature"` with a string value.
+ A `"num_words"` with a number value.
