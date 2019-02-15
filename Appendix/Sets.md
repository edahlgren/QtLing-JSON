---
layout: default
title: Sets
nav_order: 2
parent: Appendix
---

# Sets

#### Stems

+ [Protostems](#protostems)

#### Signatures

+ [Presignatures](#presignatures)
+ [Signature quadruples](#signature-quadruples)
+ [Doomed signatures](#doomed-signatures)

#### Misc

+ [Word parts ("parses")](#word-parts)
+ [Hypotheses](#hypotheses)

---

#### Protostems

---

Defined in [Phase 1: Find protostems (Output 1.2)](../Phase1/FindProtostems.html#output-12).

A JSON formatted file containing the set of all protostems.

```
{
    "protostems": [
         "[a-z]+",
         ...
     ]
}
```

Each string in the "protostems" array is the name of a protostem.

---

#### Presignatures

---

Defined in [Phase 1: Find presignatures (Output 2.2)](../Phase1/FindPresignatures.html#output-22).

A JSON formatted file containing a set of presignatures and their component affixes.

```
{
    "presignatures": [
        {
            "sig": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

For each JSON object in the "presignatures" array:

+ A `"sig"` field with a string value that is a presignature (affixes joined with `"="`).
+ An `"affixes"` field with an array value that is the set of affixes that make up the presignature.

---

#### Signature quadruples

---

Defined in [Phase 1: Find signatures (Output 1.3)](../Phase1/FindSignatures.html#output-13).

A JSON formatted file containing a set of signatures.

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

For each JSON object in the "signatures" array:

+ A `"sig"` field with a string value that is a signature, as it would appear in a word's parse triple.
+ A "stem" field with a string value that is a stem, as it would appear in a word's parse triple.
+ An "affix" field with a string value that is an affix (prefix or suffix), as it would appear in a word's parse triple.
+ A `"word"` field with a string that value that is a word, where the above fields are its parse triple.

---

#### Doomed signatures

---

Defined in [Phase 2: Generate hypotheses (Output 1.3)](../Phase2/GenerateHypotheses.html#output-13).

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

#### Word parts

---

Defined in [Phase 1: Find word parts (Output 1.3)](../Phase1/FindWordParts.html#output-13).

A JSON formatted file containing the parts (stem, affix) of each word.

```
{
    "word_parts": [
        {
            "stem": "[a-z]+",
            "affix": "[a-z]+",
            "word": "[a-z]+"
        },
        ...
    }
}
```

For each JSON object in the "word_parts" array:

+ A `"stem"` field with a string value that is the word stem.
+ An `"affix"` field with a string value that is the word affix (prefix or suffix).
+ A `"word"` field with the full word. Optional.

---

#### Hypotheses

---

Defined in [Phase 2: Generate hypotheses (Output 3.3)](../Phase2/GenerateHypotheses.html#output-33).

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
