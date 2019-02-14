---
layout: default
title: Create complex graph edges
parent: Phase 2
nav_order: 9
---

# Create complex graph edges

TODO: add description

+ [Input: simple graph edges](#input)
+ [Output: complex graph edges](#output)

---

## Input

A JSON formatted file containing a list of simple graph edges.

```
{
    "simple_edges": [
        {
            "signature1": "[a-z]+",
            "stem1": "[a-z]+",
            "signature2": "[a-z]+",
            "stem2": "[a-z]+",
            "morph": "[a-z]+",
            "word": "[a-z]+"
        },
        ...
    ]
}    
```

See [Find simple graph edges (output)](./FindSimpleGraphEdges.html#output) for more details.

---

## Output

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

For each object in the "complex_edges" array:

+ A `"signature1"` with a string value that is the first vertex of the edge.
+ A `"signature2"` with a string value that is the second vertex of the edge.
+ A `"morph"` with a string value that is a morpheme.
+ A `"word"` with a string value that is a word.
+ A `"stems"` array, where for each object:
  + A `"word"` with a string value.
  + A `"stem1"` with a string value.
  + A `"stem2"` with a string value.
