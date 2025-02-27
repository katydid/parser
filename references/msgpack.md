# Message Pack

## Basic Types

* Nil
* Boolean

## String Types

* String

## Byte Array Types

* Binary

## Float64 Types

* Float represents a IEEE 754 double precision floating point number including NaN and Infinity (float 32/64) (Big Endian 32-bit and 64-bit IEEE 754 floating-point numbers)

## Uint64 Types

* uint 8/16/32/64 (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* positive fixint (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)

## Int64 Types

* int 8/16/32/64 (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* negative fixint (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)

## Timestamp Types

* Timestamp represents an instantaneous point on the time-line in the world that is independent from time zones or calendars. Maximum precision is nanoseconds. (32-bit, 64-bit, and 96-bit UNIX seconds and nanoseconds Epoch timestamps)

## Referenced

* Nil represents nil
* Boolean represents true or false
* String extending Raw type represents a UTF-8 string
* Binary extending Raw type represents a byte array (bin 8/16/32)
* Float represents a IEEE 754 double precision floating point number including NaN and Infinity (float 32/64) (Big Endian 32-bit and 64-bit IEEE 754 floating-point numbers) 
* positive fixint (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* uint 8/16/32/64 (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 7-bit, 8-bit, 16-bit, 32-bit, and 64-bit unsigned integers)
* negative fixint (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* int 8/16/32/64 (Integer represents an integer (a value of an Integer object is limited from -(2^63) upto (2^64)-1)) (Big Endian 5-bit, 8-bit, 16-bit, 32-bit, and 64-bit Two’s Complement signed integers)
* Timestamp represents an instantaneous point on the time-line in the world that is independent from time zones or calendars. Maximum precision is nanoseconds. (32-bit, 64-bit, and 96-bit UNIX seconds and nanoseconds Epoch timestamps)
* Array represents a sequence of objects (fixarray or array 16/32)
* Map represents key-value pairs of objects (fixmap or map 16/32)
* Extension represents a tuple of type information and a byte array where type information is an integer whose meaning is defined by applications or MessagePack specification (fixext or ext 8/16/32)

### References

* https://github.com/msgpack/msgpack/blob/master/spec.md#formats
* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"