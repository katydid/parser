# Compound Types

We have concluded that all parsers require only the following compound types:

* List
* Map

Note the keys in a map are not gauranteed to be unique, for example when parsing XHTML you can multiple `div` keys in the same `body`.

## Survey

We did a [survey](./survey/Readme.md) and found that the following common compound types, which we have mapped to the supported compound types:

<table>
<tr><th>Surveyed</th><th>Supported</th></tr>
<tr><td>Void</td><td>Object (`{}`)</td></tr>
<tr><td>List</td><td>List</td></tr>
<tr><td>Set</td><td>List</td></tr>
<tr><td>Union</td><td>Not a compound, just the single value or key and value for tagged unions</td></tr>
<tr><td>Object</td><td>Map</td></tr>
<tr><td>Map</td><td>Map</td></tr>
</table>

Note: YAML also has `pairs`, which can be treated as lists of length 2.