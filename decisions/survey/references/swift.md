# Swift

## Int64

> Int64: Accommodates signed integers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807

## Float64

> Types that conform to the FloatingPoint protocol provide most basic (clause 5) operations of the IEEE 754 specification. The base, precision, and exponent range are not fixed in any way by this protocol, but it enforces the basic requirements of any IEEE 754 floating-point type.

## Decimal

BigDecimal:

> Arbitrary-precision decimal arithmetic in Swift with full math functions and fixed-precision Decimal 32-, 64-, and 128-bit types.

## Time

Swift seems to support RFC 3339, but Swift seems to truncate and only include milliseconds:

```swift
import Foundation

let dateString = "2025-06-24T16:49:32.123456789Z"
let formatter = DateFormatter()
formatter.dateFormat = "yyyy-MM-dd'T'HH:mm:ss.SSSSSSSSSX"
formatter.locale = Locale(identifier: "en_US_POSIX")
formatter.timeZone = TimeZone(secondsFromGMT: 0)

if let date = formatter.date(from: dateString) {
    // Now create a formatter to extract the seconds
    let secondsFormatter = DateFormatter()
    secondsFormatter.dateFormat = "ss.SSSSSSSSS"
    secondsFormatter.locale = Locale(identifier: "en_US_POSIX")
    secondsFormatter.timeZone = TimeZone(secondsFromGMT: 0)
    
    let secondsString = secondsFormatter.string(from: date)
    print("Seconds: \(secondsString)")  // → "32.123"
} else {
    print("Failed to parse date")
}
$ Seconds: 32.123000000
```

## References

* [Apple Developer DateFormatter](https://developer.apple.com/documentation/foundation/dateformatter)
* [Swift Fiddle DateFormatter](https://swiftfiddle.com/p42py4ojxbb7zpi2zofcmiuada)
* [Swift withfractionalseconds option](https://developer.apple.com/documentation/foundation/iso8601dateformatter/options/withfractionalseconds)
* [Unraveling Int16, Int32, and Int64 in Swift](https://appmakers.substack.com/p/differences-int16-int32-int64-swift)
* [FloatingPoint](https://developer.apple.com/documentation/swift/floatingpoint)
* [BigDecimal](https://github.com/mgriebling/BigDecimal)