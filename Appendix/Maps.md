---
layout: default
title: Maps
nav_order: 1
parent: Appendix
---

# Maps

#### Stems

+ [Protostems to words](#protostems-to-words)
+ [Stems to affix lists](#stems-to-affix-lists)

#### Words

+ [Words to signature triples](#words-to-signature-triples)

#### Signatures

+ [Signatures to affixes](#signatures-to-affixes)
+ [Signatures to stems](#signatures-to-stems)
+ [Signatures to stem entropy](#signatures-to-stem-entropy)
+ [Signatures to containment lists](#signatures-to-containment-lists)
+ [Signatures to robustness](#signatures-to-robustness)

---

#### Protostems to words

---

Defined in [Phase 1: Find protostems (Output 2.3)](../Phase1/FindProtostems.html#output-23).

A map of protostems to start and end indexes in a word list.

```
{
    "protostem_to_words": {
        "[a-z]+": {
            "word_end_index": [0-9]+,
            "word_start_index": [0-9]+
        },
        ... 
     },
     "wordlist": "/path/to/words.json"
}
```

For each field in the "protostem_to_words" object:

+ The field name is a protostem.
+ The value is a JSON object containing:
  + A `"word_start_index"` with a numeric value that is the start index in a word list.
  + A `"word_end_index"` with a numeric value that is the end index in a word list.

The `"wordlist"` points to a JSON file containing a word list.

---

#### Stems to affix lists

---

Defined in [Phase 1: Find presignatures (Output 1.2)](../Phase1/FindPresignatures.html#output-12).

A JSON formatted file containing a mapping of stems to affixes.

```
{
    "stems_to_affixes": [
        {
            "stem": "[a-z]+",
            "affixes": [
                "[a-z]+",
                ...
            ],
        },
        ...
    }
}
```

For each JSON object in the "stems_to_affixes" array:

+ A `"stem"` field with a string value that is a word stem.
+ An `"affixes"` field with an array value that is the set of affixes that the stem (above) is found with.

---

#### Signatures to affixes

---

Defined in [Phase 1: Find signatures (Output 4.2)](../Phase1/FindSignatures.html#output-42).

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

For each field in the "signatures_to_affixes" object:

+ The field name is a signature.
+ The value is a list of affixes associated with the signature.

---

#### Signatures to stems

---

Defined in [Phase 1: Find signatures (Output 5.2)](../Phase1/FindSignatures.html#output-52).

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

For each field in the "signatures_to_stems" JSON object:

+ The field name is a signature.
+ The value is a list of stems associated with the signature.

---

#### Words to signature triples

---

Defined in [Phase 1: Find signatures (Output 6.2)](../Phase1/FindSignatures.html#output-62).

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

For each field in the "words_to_triples" JSON object:

+ The field name is a word.
+ The value is an array of objects, where each object contains a signature, stem, and affix triple.

---

#### Signatures to stem entropy

---

Defined in [Phase 1: Calculate stem entropy (Output 1.2)](../Phase1/CalculateStemEntropy.html#output-12).

A JSON formatted file containing a mapping of signatures to stem entropy.

```
{
    "stem_entropy": {
        "[a-z]+": [0-9]+,
        ...
    }
}
```

For each field in the "stem_entropy" JSON object:

+ The field name is a signature.
+ The value is the signature's stem entropy.

---

#### Signatures to containment lists

---

Defined in [Phase 1: Find containment lists (Output 2.3)](../Phase1/FindContainmentLists.html#output-23).

A JSON formatted file containing a mapping of signatures to containment lists.

```
{
    "containment_lists": {
        "[a-z]+": [
            "[a-z]+",
            ...
        ],
        ...
    }
}
```

For each field in the `"containment_lists` object:

+ The field is a signature.
+ The value is an array of signatures (a containment list).

---

#### Signatures to robustness

---

Defined in [Phase 1: Calculate robustness (Output 1.3)](../Phase1/CalculateSignatureRobustness.html#output-13).

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
