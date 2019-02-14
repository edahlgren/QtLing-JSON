---
layout: default
title: Find simple graph edges
parent: Phase 2
nav_order: 8
---

# Find simple graph edges

TODO: add description

+ [Input: mapping of words to signature triples](#input)
+ [Output: simple graph edges](#output)

---

## Input

A JSON formatted file containing a mapping of words to signature triples.

```
{
    "words_to_triples": {
        "[a-z]+": [
            {
                "signature": "[a-z]+",
                "stem": "[a-z]+",
                "affix": "[a-z]+"
            },
            ...
        ],
        ...
    }
}
```

See [Map words to signature triples](../Phase1/MapWordsToSignatureTriples.html) for more details.

---

# Output

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

For each object in the "simple_edges" array:

+ A `"signature1"` with a string value that is the first vertex of the edge.
+ A `"stem1"` with a string value that is a stem of `"signature1"`.
+ A `"signature2"` with a string value that is the second vertex of the edge.
+ A `"stem2"` with a string value that is a stem of `"signature2"`.
+ A `"morph"` with a string value that is a morpheme.
+ A `"word"` with a string value that is a word.
