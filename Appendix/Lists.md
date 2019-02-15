---
layout: default
title: Lists
nav_order: 3
parent: Appendix
---

# Lists

#### Sorted lexicographically

+ [Words](#words-sorted-lexicographically)

#### Sorted by count

+ [Affixes](#affixes-sorted-by-count)
+ [Stems](#stems-sorted-by-count)

#### Graph edges

+ [Simple graph edges](#simple-graph-edges)
+ [Complex graph edges](#complex-graph-edges)

---

#### Words sorted lexicographically

---

Defined in [Preprocessing (Output 1.2)](../Preprocessing.html#output-12).

A JSON formatted file containing an array of lowercased sorted words and their frequencies.

To find suffixes, words must be ordered lexigraphically. To find prefixes, words must be ordered lexigraphically when they are reversed.

```
{
    "words": [
        {
            "name": "[a-z]+"
            "count": [0-9]+,
        },
        ...
    ]
}
```

For each JSON object in the "words" array:

+ A `"name"` field with a string value that is the lowercased word.
+ A `"count"` field with a numeric value that is the frequency of the word. Should default to 1.

---

#### Affixes sorted by count

---

Defined in [Phase 1: Find signatures (Output 2.2)](../Phase1/FindSignatures.html#output-22).

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

For each JSON object in the "affixes" array:

+ An `"affix"` field with a string value that is an affix (prefix or suffix).
+ A `"count"` field with a number value that is the frequency of the affix in a set of signatures.

---

#### Stems sorted by count

---

Defined in [Phase 1: Find signatures (Output 3.2)](../Phase1/FindSignatures.html#output-32).

A JSON formatted file containing a list of stems sorted by their frequency in a set of words associated with signatures.

```
{
    "stems": [
        {
            "stem": "[a-z]+"
            "count": [0-9]+,
        },
        ...
    ]
}
```

For each JSON object in the "stems" array:

+ A `"stems"` field with a string value that is a stem.
+ A `"count"` field with a number value that is the frequency of the stem in a set of words associated with signatures.

---

#### Simple graph edges

---

Defined in [Phase 2: Compute signature graph (Output 1.2)](../Phase2/ComputeSignatureGraph.html#output-12).

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

---

#### Complex graph edges

---

Defined in [Phase 2: Compute signature graph (Output 2.2)](../Phase2/ComputeSignatureGraph.html#output-22).

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
