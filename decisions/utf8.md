# UTF8

There are a few types that map to strings:

* '"': String (String)
* '/': Decimal (String)
* 'T': Date Time ISO 8601 (String)
* '#': Custom Tag (String)

We decided to encode all of these as UTF8.

There are two reasons:

1. Most strings would just need ascii, for example Decimal strings and Date Time ISO 8601 strings.
2. All binary serialization formats only support UTF8, while it is also the default of most text serialization formats (see our survey on [strings](./survey/string.md)).