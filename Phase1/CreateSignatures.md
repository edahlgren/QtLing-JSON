---
layout: default
title: Create signature quadruples
parent: Phase 1
nav_order: 6
---

# Create signature quadruples

TODO: Add description

+ [Input 1: word list](#input-1)
+ [Input 2: presignatures](#input-2)
+ [Output: signature quadruples](#output)

---

## Input 1

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

See [Preprocessing (output)](../Preprocessing.html#output) for more details.

## Input 2

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

See [Create presignatures (output)](./CreatePresignatures.html#output) for more details.

---

## Output

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
