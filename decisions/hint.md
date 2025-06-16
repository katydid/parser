# Hint

The `Hint` provides a hint about the location in the structure.

We conducted a [survey of of the most common serialization formats](./survey/Readme.md) and found that a limited amount of Compound types need to be supported:

* Map
* List

Note the keys in a map are not gauranteed to be unique, for example when parsing XHTML you can multiple `div` keys in the same `body`.

This results in only a limited amount of hints that are required for the user to know if it wants to `Skip`, parse the `Token` or move onto the `Next` element.

In some implementation languages, `Hint` can be indicated with a single byte or ascii character:

* '[': List Opened
* ']': List Closed
* '{': Map Opened
* '}': Map Closed
* 'k': Map Key
* 'v': Map Value or List Element, that is not an Object or List.

In other languages a sum type/enum is preferred to represent `Hint`.

## Survey

We did a [survey](./survey/Readme.md) and found that the following common compound types, which we have mapped to the supported compound types:

<table>
<tr><th>Surveyed</th><th>Supported As</th></tr>
<tr><td>Void</td><td>Object (`{}`)</td></tr>
<tr><td>List</td><td>List</td></tr>
<tr><td>Set</td><td>List</td></tr>
<tr><td>Union</td><td>Not a compound, just the single value or key and value for tagged unions</td></tr>
<tr><td>Object</td><td>Map</td></tr>
<tr><td>Map</td><td>Map</td></tr>
</table>

Note: YAML also has `pairs`, which can be treated as lists of length 2.

## Why Next returns a Hint and not a Token

The `Next` method returns a hint.

```
Next : () -> (Hint | error | EOF)
```

Using this `Hint` the user can decide to `Skip` or parse the `Token`.
Only the `Token` method will parse the actual key or value:

```
Token: () -> ((Kind, value) | error)
```

The question is why would we want to separate this two methods and not just have a single `NextToken` method:

```
Token: () -> ((Kind, value) | error | EOF)
```

The answer is CPU and memory efficiency.
We want the user to have as much control as possible over what actually gets parsed.
This way the user can efficient call `Skip` or `Next` to skip over what does not need parsing.

Note that tokenizing can be especially expensive as it can result in allocating memory, 
for example when unquoting a JSON string.
This means we should only tokenize values the user really cares about.

The reason performance is important is that in validation languages that are optimized properly the parser becomes the bottleneck.
When applying a validator as a filter through millions of record of serialized data, we want to have good reasons for being the bottleneck.