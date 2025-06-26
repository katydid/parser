# Ruby

## Time

Ruby supports RFC 3339:

```ruby
DateTime.rfc3339('2001-02-03T04:05:06+07:00')
```

Ruby also supports nanoseconds:

```ruby
DateTime.parse('2001-02-03T04:05:06.123456789+07:00').iso8601(9)
```

## References

* [Rubydoc.info Method: DateTime.rfc3339](https://www.rubydoc.info/stdlib/date/DateTime.rfc3339)
* [Rubydoc.info Class: DateTime](https://www.rubydoc.info/stdlib/date/DateTime)