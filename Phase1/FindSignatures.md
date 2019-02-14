---
layout: default
title: Find signatures
parent: Phase 1
nav_order: 4
---

# Find signatures

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405).

Substeps:

+ [Create signature quadruples](#create-signature-quadruples)
+ [Sort affixes](#sort-affixes)
+ [Sort stems](#sort-stems)
+ [Map signatures to affixes](#map-signatures-to-affixes)
+ [Map signatures to stems](#map-signatures-to-stems)
+ [Map words to signature triples](#map-words-to-signature-triples)

---

#### Create signature quadruples

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is the first part of [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405).

This step creates signature quadruples from presignatures and a sorted word list. A signature quadruple is a stem, affix, signature string, and word.

It is based on [CLexicon::step4b_link_signature_and_stem_and_word()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L533) -> [CWord::add_parse_triple](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/Word.cpp#L32). 

Other useful structures can easily be derived from the quadruples (see substeps).

+ [Input: a sorted word list](#input-11)
+ [Input: a set of presignatures](#input-12)
+ [Output: a set of signature quadruples](#output-13)

---

#### Input 1.1

---

A JSON formatted file containing an array of lowercased sorted words and their frequencies.

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

See [Preprocessing (Output 1.2)](../Preprocessing.html#output-12) for more details.

---

#### Input 1.2

---

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

See [Find presignatures (Output 2.2)](./FindPresignatures.html#output-22) for more details.

---

#### Output 1.3

---

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

#### Sort affixes

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is a side effect of [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405)

This step is a simple transformation of [signature quadruples](#output-13). The result is a list of all affixes sorted by their frequency in the signature quadruples.

This step can be executed in parallel with all other simple transformations of signature quadruples.

+ [Input: a set of signature quadruples](#input-21)
+ [Output: a list of sorted affixes](#output-22)

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

See [Output 1.3](#output-13) for more details.

---

#### Output 2.2

---

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

#### Sort stems

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is a side effect of [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405)

This step is a simple transformation of [signature quadruples](#output-13). The result is a list of all stems sorted by their frequency in the words of signature quadruples.

This step can be executed in parallel with all other simple transformations of signature quadruples.

+ [Input: a set of signature quadruples](#input-31)
+ [Output: a list of sorted stems](#output-32)

---

#### Input 3.1

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

See [Output 1.3](#output-13) for more details.

---

#### Output 3.2

---

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

#### Map signatures to affixes

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is a side effect of [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405)

This step is a simple transformation of [signature quadruples](#output-13). The result is a mapping of signatures to affixes.

This step can be executed in parallel with all other simple transformations of signature quadruples.

+ [Input: a set of signature quadruples](#input-41)
+ [Output: a map of signatures to affixes](#output-42)

---

#### Input 4.1

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

See [Output 1.3](#output-13) for more details.

---

#### Output 4.2

---

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

#### Map signatures to stems

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is a side effect of [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405)

This step is a simple transformation of [signature quadruples](#output-13). The result is a mapping of signatures to stems.

This step can be executed in parallel with all other simple transformations of signature quadruples.

+ [Input: a set of signature quadruples](#input-51)
+ [Output: a map of signatures to stems](#output-52)

---

#### Input 5.1

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

See [Output 1.3](#output-13) for more details.

---

#### Output 5.2

---

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

#### Map words to signature triples

---

In [QtLing](https://github.com/edahlgren/QtLing/tree/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing) this is a side effect of [CLexicon::step4_create_signatures()](https://github.com/edahlgren/QtLing/blob/6df4bf4898274a26db7fc961f4cc7e8f7c0a91eb/QtLing/lexicon_crab1.cpp#L405)

This step is a simple transformation of [signature quadruples](#output-13). The result is a mapping of words to signature triples. A signature triple is a signature string, stem, and affix.

This step can be executed in parallel with all other simple transformations of signature quadruples.

+ [Input: a set of signature quadruples](#input-61)
+ [Output: a map of words to signature triples](#output-62)

---

#### Input 6.1

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

See [Output 1.3](#output-13) for more details.

---

#### Output 6.2

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

For each field in the "words_to_triples" JSON object:

+ The field name is a word.
+ The value is an array of objects, where each object contains a signature, stem, and affix triple.
