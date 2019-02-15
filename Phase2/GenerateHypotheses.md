---
layout: default
title: Generate hypotheses
parent: Phase 2
nav_order: 5
---

# Generate hypotheses

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step9_from_sig_graph_edges_map_to_hypotheses()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/hypothesis.cpp#L37).

Substeps:

+ [Find doomed signatures](#find-doomed-signatures)
+ [Find doomed word parts](#find-doomed-word-parts)
+ [Find presignatures](#find-presignatures)
+ [Find signatures](#find-signatures)
+ [Create hypotheses](#create-hypotheses)

---

#### Find doomed signatures

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is the main for-loop of [CLexicon::step9_from_sig_graph_edges_map_to_hypotheses()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/hypothesis.cpp#L37).

This step finds a set of "doomed" signatures from complex graph edges and signature stem entropy.

+ [Input: a list of complex graph edges](#input-11)
+ [Input: a map of signatures to stem entropy](#input-12)
+ [Output: a set of doomed signatures](#output-13)

---

#### Input 1.1

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

See [Compute signature graph (Output 2.2)](./ComputeSignatureGraph.html#output-22) for more details.

---

#### Input 1.2

---

A JSON formatted file containing a mapping of signatures to stem entropy.

```
{
    "stem_entropy": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

See [Calculate stem entropy (Output 1.2)](../Phase1/CalculateStemEntropy.html#output-12) for more details.

---

#### Output 1.3

---

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

---

#### Find doomed word parts

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step9a_from_doomed_info_map_to_parses()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/hypothesis.cpp#L174).

This step finds word parts ("parses") from a set of "doomed" signatures.

+ [Input: a set of signature quadruples](#input-21)
+ [Input:: a set of doomed signatures](#input-22)
+ [Output: a set of word parts](#output-23)

---

#### Input 2.1

---

A JSON formatted file containing a set of signature quadruples.

```
{
    "signatures": [
        {
            "sig": "[a-z]+",
            "stem": "[a-z]+",
            "affix": "[a-z]+",
            "word": "[a-z]+"
        },
        ...
    }
}
```

See [Find signatures (Output 1.3)](../Phase1/FindSignatures.html#output-13) for more details.

---

#### Input 2.2

---

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

See [Output 1.3](#output-13) for more details.

---

#### Output 2.3

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

#### Find presignatures

---

Redo [Find presignatures](../Phase1/FindPresignatures.html) from Phase 1.

---

#### Find signatures

---

Redo [Find signatures](../Phase1/FindSignatures.html) from Phase 1.

---

#### Create hypotheses

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step9c_from_doomed_info_map_to_hypotheses()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/hypothesis.cpp#L291).

This step generates morphological hypothesis structures from doomed signatures and an edges list.

+ [Input: a list of complex graph edges](#input-31)
+ [Input: a set of doomed signatures](#input-32)
+ [Output: a set of hypotheses](#output-33)

---

#### Input 3.1

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

See [Compute signature graph (Output 2.2)](./ComputeSignatureGraph.html#output-22) for more details.

---

#### Input 3.2

---

A JSON formatted file containing "doomed" signatures.

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

See [Output 1.3](#output-13) for more details.

---

#### Output 3.3

---

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
