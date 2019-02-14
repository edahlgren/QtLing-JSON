---
layout: default
title: Map words to signature triples
parent: Create signature quadruples
nav_order: 5
---

# Map words to signature triples

TODO: Add description

+ [Input: signature quadruples](#input)
+ [Output: mapping of words to signature triples](#output)

---

## Input

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

See [Create signatures (output)](../CreateSignatures.html#output) for more details.

## Output

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
