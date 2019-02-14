---
layout: default
title: Find doomed signatures
parent: Phase 2
nav_order: 10
---

# Find doomed signatures

TODO: add description

+ [Input 1: complex graph edges](#input-1)
+ [Input 2: mapping of signatures to stem entropy](#input-2)
+ [Output: doomed signatures](#output)

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

A JSON formatted file containing a mapping of signatures to stem entropy.

```
{
    "stem_entropy": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

See [Calculate stem entropy](./CalculateStemEntropy.html#output) for more details.

---

## Output

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

For each field in the "doomed_signatures" JSON object:

+ The field name is a "doomed" signature.
+ The field value is an object that contains:
  + A `"edgeId"` with a number value that is an edgeId in a complex edges list.
  + A `"doomed_affixes"` with an array value that contains "doomed" affixes.

The `"edges"` field has a string value that is a path to a JSON formatted file containing the list of complex edges of input 1.
