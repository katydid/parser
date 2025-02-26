# Message Pack

* Nil
* Boolean
* String
* Binary

## String Types

* String

## Byte Array Types

* Binary

## Referenced

* Nil represents nil
* Boolean represents true or false
* String extending Raw type represents a UTF-8 string
* Binary extending Raw type represents a byte array (bin 8/16/32)
* Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1) (positive fixint, negative fixint, int 8/16/32/64 or uint 8/16/32/64)
* Float represents a IEEE 754 double precision floating point number including NaN and Infinity (float 32/64)
* Array represents a sequence of objects (fixarray or array 16/32)
* Map represents key-value pairs of objects (fixmap or map 16/32)
* Extension represents a tuple of type information and a byte array where type information is an integer whose meaning is defined by applications or MessagePack specification (fixext or ext 8/16/32)
* Timestamp represents an instantaneous point on the time-line in the world that is independent from time zones or calendars. Maximum precision is nanoseconds.

### References

* https://github.com/msgpack/msgpack/blob/master/spec.md#formats