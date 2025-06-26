# PHP

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

## References

* [google-cloud-php TimeTrait](https://github.com/googleapis/google-cloud-php/blob/main/Core/src/TimeTrait.php)
* [](https://3v4l.org/FPHoh)