# Tree

Our parser is a pull-based parser, but the parse tree still needs an underlying model of what we imagine the parse tree would look like, if we would parse it fully into memory.

## Haskell Data.Tree

This model is based on a [Haskell Data.Tree](https://hackage-content.haskell.org/package/containers-0.8/docs/src/Data.Tree.html#Tree):

```haskell
data Tree a = Node {
    rootLabel :: a,         -- ^ label value
    subForest :: [Tree a]   -- ^ zero or more child trees
}
```

We will refer to the `rootLabel` as the `label` or `key` going forward.
We will refer to the `subForest` as `children` going forward.

The generic parameter `a` would be replaced with a `Token`:

```haskell
data Token =
  | Null -- '_'
  | False -- 'f'
  | True -- 't'
  | Bytes ByteString -- 'x'
  | String Text -- '"'
  | Int64 Int64 -- '-'
  | Float64 Double -- '.'
  | Decimal Text -- '/'
  | Nanoseconds Int64 -- '9'
  | DateTime Text -- 'T'
  | Tag Text -- '#'
```

This means that our parse tree is a `Tree Token`, but with our renamings we will redefine the type for convenience:

```haskell
data ParseTree = Node {
    label :: Token,
    children :: [ParseTree]
}
```

Our pull based parser would see every:
* `Node v []` as a value and return a `Hint` = `v`
* `Node k (c::cs)` as a key and return a `Hint` = `k` with `Hint`s `{` and `}` surrounding the list of children.

## Example JSON

We can imagine JSON would parse into our ParseTree.

Given the following JSON:
```json
{"a": 1, "b": [2, {"c:" 3, "d": 4}]}
```

It would parse into our parse tree as:
```haskell
[
    Node (String "a") [
        Node (Int64 1) []
    ],
    Node (String "b") [
        Node Null [
            Node (Int64 2) []
        ],
        Node Null [
            Node (String "c") [
                Node (Int64 3) []
            ],
            Node (String "d") [
                Node (Int64 4) []
            ]
        ]
    ]
]
```

Remeber every `Node v []` would parse as a `Hint`: `v`,
while every `Node k children`, where `children != []`, would parse as a `Hint`: `k` with `{` and `}` `Hint`s surrounding the list of children.

This means our pull-based parser would parse it as:
```
{"a": 1, "b": {null: 2, null: {"c": 3, "d": 4}}}
```

Or more verbosely:
```
Next -> '{'
Next -> 'k'
Token -> '"', "a"
Next -> 'v'
Token -> '-', 1
Next -> 'k'
Token -> '"', "b"
Next -> '{'
Next -> 'k'
Token -> '_'
Next -> 'v'
Token -> '-', 2
Next -> 'k'
Token -> '_'
Next -> '{'
Next -> 'k'
Token -> '"', "c"
Next -> 'v'
Token -> '-', 3
Next -> 'k'
Token -> '"', d
Next -> 'v'
Token -> '-', 4
Next -> '}'
Next -> '}'

