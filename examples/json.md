## JSON

**TODO: Update to new interface**

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

Next -> 'F'
Token -> ('"', "int")
Next -> 'V'
Token -> ('-', 1)

Next -> 'F'
Token -> ('"', "bool")
Token -> 't'

Next -> 'F'
Token -> ('"', "arr")
Next -> '['
Next -> 'V'
Token -> ('"', "elem")
Next -> ']'

Next -> '}'
```

We can also look at this JSON object as translating to the following list of Trees, where a `Tree` is `Label` and a list of `Children` of type `Tree`:

```haskell
[
  {
    "Label": "int",
    "Children": [
      {
        "Label": 1,
        "Children": []
      }
    ]
  },
  {
    "Label": "bool",
    "Children": [
      {
        "Label": true,
        "Children": []
      }
    ]
  },
  {
    "Label": "arr",
    "Children": [
      {
        "Label": (),
        "Children": [
          {
            "Label": "elem",
            Children: [],
          }
        ]
      }
    ]
  }
]
```

Note that each element in the array will be tree with a `Label` equal to unit and this will be skipped over by the parser for convenience.

## Next and Skip Example

In the previous example we only covered Next and Token.
In this example we also look at what happens when we call Skip in various locations.

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

Next -> 'F'
Token -> ('"', "num")
Next -> 'V'
Token -> ('.', 3.14)

Next -> 'F'
Token -> ('"', "arr")
Next -> '['
Next -> 'V'
Token -> '_'
Next -> 'V'
Token -> 't'
Next -> 'V'
Token -> 'f'
Next -> 'V'
Token -> 't'
Next -> 'V'
Token -> ('-', 1)
Skip

Next -> 'F'
Token -> ('"', "obj")

Next -> '{'
Next -> 'F'
Token -> ('"', "key")
Next -> 'V'
Token -> ('"', "val")
Next -> 'F'
Token -> ('"', "nums")
Skip // skips the whole array in "nums"

Skip // skips the rest of the object in "obj"

Next -> '}'
Next -> EOF
```
