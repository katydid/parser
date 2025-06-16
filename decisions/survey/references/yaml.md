## YAML

## Basic Types

* null
* bool

## String Types

* str

## Byte Array Types

* binary

## Decimal Types

* int: However, there are cases where an integer provided may overflow the native type’s storage capability. In this case, the processor should find some manner to round-trip the integer, perhaps using a string based representation.
* float: The valid range and accuracy depends on the implementation, though 32 bit IEEE floats should be safe.

## Float64 Types

* float: The valid range and accuracy depends on the implementation, though 32 bit IEEE floats should be safe.

## Int64 Types

* int: However, there are cases where an integer provided may overflow the native type’s storage capability. In this case, the processor should find some manner to round-trip the integer, perhaps using a string based representation.

## Timestamp Types

* timestamp

## List Types

* seq
* pairs

## Set Types

* set

## Map Types

* map
* omap

## Object Types

* map
* omap

## Referenced

* null
* bool
* str
* binary
* int: However, there are cases where an integer provided may overflow the native type’s storage capability. In this case, the processor should find some manner to round-trip the integer, perhaps using a string based representation.
* float: The valid range and accuracy depends on the implementation, though 32 bit IEEE floats should be safe.
* timestamp
* seq
* set
* map (- 2001-07-23 ? [ New York Yankees,Atlanta Braves ] : [ 2001-07-02, 2001-08-12, 2001-08-14] -- mapping between sequences)
* omap (ordered map)
* merge (used to merge two messages, not a type)
* value (used for default values, not a type)
* yaml (encoding yaml in yaml, not a type)
* pairs

### References

* https://yaml.org/type/
* https://www.tutorialspoint.com/yaml/yaml_collections_and_structures.htm
* https://tutorialreference.com/yaml/datatypes/advanced/yaml-pairs
* https://stackoverflow.com/questions/24090177/how-to-merge-yaml-arrays#57209078