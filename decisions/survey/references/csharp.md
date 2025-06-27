# C Sharp

## Int64

> The long data type can store whole numbers from -9223372036854775808 to 9223372036854775807.

## Float64

> C# has IEEE 754 single and double precision types supported by keywords:

## Decimal

> C# has a 128 bit limited-precision decimal type denoted by the keyword decimal

BigDecimal is a github project:

> An arbitrary-precision decimal (base 10) floating-point number class. Over 4.5 million downloads on NuGet!

## Time

OffsetDateTime
RFC 3339 pattern (extended ISO but with offset in form +/-HH:mm or Z), optional calendar
`<value calendar="Gregorian 3">2013-07-26T16:45:20.123456789+01:00</value>`

## Sum

> Now that I have defined the different variants of our Payment type, I now define the Payment type using the OneOf library as shown below.

```csharp
public enum CardType { ATM, Debit, Credit }

[Union]
public interface Payment
{
    Payment Cash(decimal amount);
    Payment Card(CardNumber number,  CardType cardType, Amount amount);
    Payment Cheque(ChequeNumber number,  OwnerName ownerName, Amount amount);
}
```

> Now that we have defined our Payment type.

```csharp
public static Amount GetAmount(Payment payment)
    => payment switch {
        Cash cash => cash.Amount,
        Card card => card.Amount,
        Cheque cheque => cheque.Amount,
            _ => 0m
    };
```

> I do this by using the Match method defined in the OneOf

## Reference

* [nodatime](https://nodatime.org/3.2.x/userguide/serialization)
* [W3Schools csharp data types](https://www.w3schools.com/cs/cs_data_types.php)
* [Floating-point cheat sheet for C#](https://floating-point-gui.de/languages/csharp/)
* [BigDecimal](https://github.com/AdamWhiteHat/BigDecimal)
* [Oneof](https://github.com/mcintyre321/OneOf)
* [Algebraic Data Types in C#](https://kasozivincent.hashnode.dev/algebraic-data-types-in-c)