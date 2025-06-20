# Tags

The Custom Tag Kind is represented as a String:

* '#': Custom Tag (String)

The parser's job is to parse a serialization format into a generic parse tree.
This tree might throw away information that is specific to the serialization format that might have been important.
We can augment our parser with Custom Tags to preserve this information.

## Example: JSON

Parsing JSON will throw away whether it was an array or an object that was parsed.

```json
"A"
{"A": []}
{"A": {}}
```

Are all represented by the following parse tree:
```haskell
Node (String "A") []
```

[JSON Schema](https://json-schema.org) requires knowing whether an object or an array was parsed.

For example, the [object data type](https://json-schema.org/understanding-json-schema/reference/object):
```json
{"type": "object"}
```

Or the [array data type](https://json-schema.org/understanding-json-schema/reference/array):
```json
{"type": "array"}
```

We can augment our parser with Custom Tags `array` and `object` to preserve this information.

Then we get three different parse trees:

The string:
```json
"A"
```

is parsed into the original:
```haskell
Node (String "A") []
```

The array:
```json
{"A": []}
```

is parsed with a custom `array` tag:
```haskell
Node (String "A") [Node (Tag "array") []]
```

The object:
```json
{"A": []}
```

is parsed with a custom `object` tag:
```haskell
Node (String "A") [Node (Tag "object") []]
```

## Example: XML

Parsing XML will throw away whether it was an element, attribute or text that was parsed.

```xml
<A><B>C</B></A>
<A><B><C/></B></A>
<A "B"="C"/>
```

```haskell
Node (String "A") [
    Node (String "B") [
        Node (String "C") []
    ]
]
```

[RelaxNG](https://relaxng.org/compact-tutorial-20030326.html) requires knowing whether an parsed node was an element, attribute or text. See for example, the following RelaxNG grammar:
```
element addressBook {
  element card {
    attribute name { text },
    attribute email { text }
  }*
}
```

We can augment our parser with Custom Tags `elem`, `attr` and `text` to preserve this information.

Then we get three different parse trees:

The "C" text:
```xml
<A><B>C</B></A>
```

is parsed with `elem` and `text` tags:
```haskell
Node (Tag "elem") [Node (String "A") [
    Node (Tag "elem") [Node (String "B") [
        Node (Tag "text") [Node (String "C") []]
    ]]
]]
```

The "C" element:
```xml
<A><B><C/></B></A>
```

is parsed with `elem` tags:
```haskell
Node (Tag "elem") [Node (String "A") [
    Node (Tag "elem") [Node (String "B") [
        Node (Tag "elem") [Node (String "C") []]
    ]]
]]
```

The "B" attribute and "C" value:
```xml
<A "B"="C"/>
```

is parsed with `elem`, `attr` and `text` tags:
```haskell
Node (Tag "elem") [Node (String "A") [
    Node (Tag "attr") [Node (String "B") [
        Node (Tag "text") [Node (String "C") []]
    ]]
]]
```