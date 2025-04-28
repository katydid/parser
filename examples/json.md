## JSON

Examples of Parsing JSON using Katydid's Parser interface.

## Basic Example

Given the following input:

```json
{
  "int": 1,
  "bool": true,
  "arr": ["elem"]
}
```

We expect the following from the parser:

```
Next -> '{'

Next -> 'k'
Token -> ('"', "int")
Next -> 'v'
Token -> ('-', 1)

Next -> 'k'
Token -> ('"', "bool")
Token -> 't'

Next -> 'k'
Token -> ('"', "arr")
Next -> '['
Next -> 'v'
Token -> ('"', "elem")
Next -> ']'

Next -> '}'
```

## Next and Skip Example

Given the following input:

```json
{
  "num": 3.14,
  "arr": [null, false, true, 1, 2, 3],
  "obj": {
    "key": "val",
    "nums": [1,2,3],
    "more":1,
    "extra":2,
  }
}
```

We expect the following from the parser:

```
Next -> '{'

Next -> 'k'
Token -> ('"', "num")
Next -> 'v'
Token -> ('.', 3.14)

Next -> 'k'
Token -> ('"', "arr")
Next -> '['
Next -> 'v'
Token -> '_'
Next -> 'v'
Token -> 't'
Next -> 'v'
Token -> 'f'
Next -> 'v'
Token -> 't'
Next -> 'v'
Token -> ('-', 1)
Skip

Next -> 'k'
Token -> ('"', "obj")

Next -> '{'
Next -> 'k'
Token -> ('"', "key")
Next -> 'v'
Token -> ('"', "val")
Next -> 'k'
Token -> ('"', "nums")
Skip // skips the whole array in "nums"

Skip // skips the rest of the object in "obj"

Next -> '}'
Next -> EOF
```
