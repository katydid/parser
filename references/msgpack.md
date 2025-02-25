# Message Pack

https://github.com/msgpack/msgpack/blob/master/spec.md#formats

* Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)
* Nil represents nil
* Boolean represents true or false
* Float represents a IEEE 754 double precision floating point number including NaN and Infinity
* String extending Raw type represents a UTF-8 string
* Binary extending Raw type represents a byte array
* Array represents a sequence of objects
* Map represents key-value pairs of objects
* Extension represents a tuple of type information and a byte array where type information is an integer whose meaning is defined by applications or MessagePack specification
* Timestamp represents an instantaneous point on the time-line in the world that is independent from time zones or calendars. Maximum precision is nanoseconds.

## Serialization: type to format conversion

* Integer	int format family (positive fixint, negative fixint, int 8/16/32/64 or uint 8/16/32/64)
* Nil	nil
* Boolean	bool format family (false or true)
* Float	float format family (float 32/64)
* String	str format family (fixstr or str 8/16/32)
* Binary	bin format family (bin 8/16/32)
* Array	array format family (fixarray or array 16/32)
* Map	map format family (fixmap or map 16/32)
* Extension	ext format family (fixext or ext 8/16/32)