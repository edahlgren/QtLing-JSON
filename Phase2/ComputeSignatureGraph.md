---
layout: default
title: Compute signature graph
parent: Phase 2
nav_order: 4
---

# Compute signature graph

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step8a_compute_sig_graph_edges()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/signature_graph.cpp#L17) and [CLexicon::step8b_compute_sig_graph_edge_map()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/signature_graph.cpp#L96).

Substeps:

+ [Map words to signature triples](#map-words-to-signature-triples)
+ [Find simple graph edges](#find-simple-graph-edges)
+ [Find complex graph edges](#find-complex-graph-edges)

---

#### Map words to signature triples

---

Redo [Map words to signature triples](../Phase1/FindSignatures.html#map-words-to-signature-triples) from Phase 1.

---

#### Find simple graph edges

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step8a_compute_sig_graph_edges()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/signature_graph.cpp#L17).

This step generates a list of "simple" graph edges where graph vertices are signatures. In a simple graph edge there is only one stem for each signature.

+ [Input: a map of words to signature triples](#input-11)
+ [Output: a list of simple graph edges](#output-12)

---

#### Input 1.1

---

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

See [Find signatures (Output 6.2)](../Phase1/FindSignatures.html#output-62) for more details.

---

#### Output 1.2

---

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

#### Find complex graph edges

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step8b_compute_sig_graph_edge_map()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/signature_graph.cpp#L96).

This step converts simple graph edges to complex ones. A complex graph edge still has signatures as vertices but also supports multiple stems.

+ [Input: a list of simple graph edges](#input-21)
+ [Output: a list of complex graph edges](#output-22)

---

#### Input 2.1

---

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

See [Output 1.2](#output-12) for more details.

---

#### Output 2.2

---

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
