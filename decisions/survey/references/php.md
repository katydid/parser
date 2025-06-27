# PHP

## Int64

This seems to be a 64 bit integer with maximum value: 9,223,372,036,854,775,807

> The size of an int is platform-dependent, although a maximum value of about two billion is the usual value (that's 32 bits signed). 64-bit platforms usually have a maximum value of about 9E18. 

## Float64

> Floating point numbers have limited precision. Although it depends on the system, PHP typically uses the IEEE 754 double precision format.

## Decimal

The BcMath\Number class:

> A class for an arbitrary precision number.

The `div` function provides confirmation that decimals are also supported.

```php
<?php
$number = new BcMath\Number('0.002');

$ret1 = $number->div(new BcMath\Number('2.000'));
$ret2 = $number->div('-3');
$ret3 = $number->div(32);

var_dump($number, $ret1, $ret2, $ret3);
?>
```

Output:

```
object(BcMath\Number)#1 (2) {
  ["value"]=>
  string(5) "0.002"
  ["scale"]=>
  int(3)
}
object(BcMath\Number)#3 (2) {
  ["value"]=>
  string(5) "0.001"
  ["scale"]=>
  int(3)
}
object(BcMath\Number)#2 (2) {
  ["value"]=>
  string(16) "-0.0006666666666"
  ["scale"]=>
  int(13)
}
object(BcMath\Number)#4 (2) {
  ["value"]=>
  string(9) "0.0000625"
  ["scale"]=>
  int(7)
}
```

## Time

php's date_parse seems to support RFC 3339, but not nanoseconds

```
<?php
date_default_timezone_set('UTC');
var_dump(date_parse("2006-12-12T10:00:00.999999999-04:00"));
```

Google-cloud-php's TimeTrait parses RFC 3339 into DateTimeImmutable which cannot contain nanos and nanos separately.

```php
/**
* Parse a Timestamp string and return a DateTimeImmutable instance and nanoseconds as an integer.
*
* @param string $timestamp A string representation of a timestamp, encoded
*        in RFC 3339 format (YYYY-MM-DDTHH:MM:SS.000000[000]TZ).
* @return array [\DateTimeImmutable, int]
* @throws \Exception If the timestamp string is in an unrecognized format.
*/
private function parseTimeString($timestamp)
{
    ...

    return [$dt, $nanos];
}
```

## Sum

PHP has a RFC for tagged unions that is still in draft status.

PHP also has unions types, but not tagged unions.

## References

* [google-cloud-php TimeTrait](https://github.com/googleapis/google-cloud-php/blob/main/Core/src/TimeTrait.php)
* [php playground with time](https://3v4l.org/FPHoh)
* [Integers](https://www.php.net/manual/en/language.types.integer.php)
* [Floating point numbers](https://www.php.net/manual/en/language.types.float.php)
* [The BcMath\Number class](https://www.php.net/manual/en/class.bcmath-number.php)
* [BcMath\Number::div](https://www.php.net/manual/en/bcmath-number.div.php)
* [PHP RFC: Tagged Unions](https://wiki.php.net/rfc/tagged_unions)
* [PHP 8.0: Union Types](https://php.watch/versions/8.0/union-types)