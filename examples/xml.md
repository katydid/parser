# XML

Examples of Parsing XML using Katydid's Parser interface.

## Basic Example

Given the following input:

```xml
<Person name="Robert">
  <BirthYear>1984</BirthYear>
  <Address number=456 street="TheStreet"/>
  <Married/>
</Person>
```

If we pass an option to our parser to ignore spaces,
then we expect the following parser execution:

```
Next -> '{'

Token -> ('"', "Person")
Next -> '{'

Next -> 'k'
Token -> ('"', "name)
Next -> 'v'
Token -> ('"', "Robert")

Next -> 'k'
Token -> ('"', "BirthYear")
Next -> 'v'
Token -> ('-', 1984)

Next -> 'k'
Token -> ('"', "Address")
Next -> '{'

Next -> 'k'
Token -> ('"', "number")
Next -> 'v'
Token -> ('-', 456)

Next -> 'k'
Token -> ('"', "street)
Next -> 'v'
Token -> ('"', "TheStreet")

Next -> '}'

Next -> 'k'
Token -> ('"', "Married")
Next -> 'v'
Token -> '_'

Next -> '}'

Next -> '}'
Next -> EOF
```

## Spaces Example

Given the following input:

```xml
<Person name="Robert">
  <BirthYear>1984</BirthYear>
  <Address number=456 street="TheStreet"/>
  <Married/>
</Person>
```

We expect the following parser execution:

```
Next -> '{'

Token -> ('"', "Person")
Next -> '{'

Next -> 'k'
Token -> ('"', "name)
Next -> 'v'
Token -> ('"', "Robert")

Next -> 'k'
Token -> ('"', "\n\t")
Next -> 'v'
Token -> '_'

Next -> 'k'
Token -> ('"', "BirthYear")
Next -> 'v'
Token -> ('-', 1984)

Next -> 'k'
Token -> ('"', "\n\t")
Next -> 'v'
Token -> '_'

Next -> 'k'
Token -> ('"', "Address")
Next -> '{'

Next -> 'k'
Token -> ('"', "number")
Next -> 'v'
Token -> ('-', 456)

Next -> 'k'
Token -> ('"', "street)
Next -> 'v'
Token -> ('"', "TheStreet")

Next -> '}'

Next -> 'k'
Token -> ('"', "\n\t")
Next -> 'v'
Token -> '_'

Next -> 'k'
Token -> ('"', "Married")
Next -> 'v'
Token -> '_'

Next -> 'k'
Token -> ('"', "\n")
Next -> 'v'
Token -> '_'

Next -> '}'

Next -> '}'
Next -> EOF
```

Notice how duplicates keys in the same Map are allowed, for example "\n\t".

## Skip Example

Given the following input:

```xml
<Person name="Robert">
  <BirthYear>1984</BirthYear>
  <Address number=456 street="TheStreet"/>
  <Married/>
</Person>
```

We expect the following parser execution:

```
Next -> '{'

Token -> ('"', "Person")
Next -> '{'

Next -> 'k'
Token -> ('"', "name)
Next -> 'v'
Token -> ('"', "Robert")

Next -> 'k'
Token -> ('"', "\n\t")
Skip

Next -> 'k'
Token -> ('"', "BirthYear")
Next -> 'v'
Token -> ('-', 1984)

Next -> 'k'
Token -> ('"', "\n\t")
Skip

Next -> 'k'
Token -> ('"', "Address")
Next -> '{'

Next -> 'k'
Token -> ('"', "number")
Skip

Skip

Next -> 'k'
Token -> ('"', "\n\t")
Skip

Next -> 'k'
Token -> ('"', "Married")
Next -> 'v'
Token -> '_'

Next -> 'k'
Token -> ('"', "\n")
Skip

Next -> '}'

Next -> '}'
Next -> EOF
```