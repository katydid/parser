# History of Serialization Formats

<table border="1">
  <thead>
    <tr>
      <th>Format</th>
      <th>Year</th>
      <th>Inventor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>GML</td>
      <td>1969</td>
      <td>IBM</td>
    </tr>
    <tr>
      <td>List-Directed Input/Output or CSV</td>
      <td>1972</td>
      <td>IBM OS/360</td>
    </tr>
    <tr>
      <td>INI</td>
      <td>1980s early</td>
      <td>Microsoft MS-DOS</td>
    </tr>
    <tr>
      <td>ASN.1</td>
      <td>1984</td>
      <td>International Telecommunication Union</td>
    </tr>
    <tr>
      <td>SGML</td>
      <td>1986</td>
      <td>ISO standard</td>
    </tr>
    <tr>
      <td>Property List</td>
      <td>1980s late</td>
      <td>Next/Apple</td>
    </tr>
    <tr>
      <td>JSON</td>
      <td>1996</td>
      <td>Netscape</td>
    </tr>
    <tr>
      <td>XML</td>
      <td>1996</td>
      <td>W3C</td>
    </tr>
    <tr>
      <td>Binary Property List</td>
      <td>2000</td>
      <td>Apple</td>
    </tr>
    <tr>
      <td>Protocol Buffers</td>
      <td>2001</td>
      <td>Google</td>
    </tr>
    <tr>
      <td>YAML</td>
      <td>2001</td>
      <td>Clark Evans</td>
    </tr>
    <tr>
      <td>Apache Thrift</td>
      <td>2006</td>
      <td>Facebook</td>
    </tr>
    <tr>
      <td>Message Pack</td>
      <td>2009</td>
      <td>Sadayuki Furuhashi</td>
    </tr>
    <tr>
      <td>Apache Avro</td>
      <td>2009</td>
      <td>Apache Hadoop</td>
    </tr>
    <tr>
      <td>Binary JSON (BSON)</td>
      <td>2009</td>
      <td>Mongo DB</td>
    </tr>
    <tr>
      <td>Smile</td>
      <td>2010</td>
      <td>FasterXML</td>
    </tr>
    <tr>
      <td>Bond</td>
      <td>2011</td>
      <td>Microsoft</td>
    </tr>
    <tr>
      <td>UBJSON</td>
      <td>2012</td>
      <td>Genuitec</td>
    </tr>
    <tr>
      <td>TOML</td>
      <td>2013</td>
      <td>Tom Preston-Werner</td>
    </tr>
    <tr>
      <td>CapnProto</td>
      <td>2013</td>
      <td>Sandstorm</td>
    </tr>
    <tr>
      <td>Apache Parquet</td>
      <td>2013</td>
      <td>Hadoop</td>
    </tr>
    <tr>
      <td>CBOR</td>
      <td>2013</td>
      <td>Carsten Bormann and Paul Hoffman (IETF)</td>
    </tr>
    <tr>
      <td>FlatBuffers</td>
      <td>2014</td>
      <td>Google/Fun Propulsion Labs</td>
    </tr>
    <tr>
      <td>FlexBuffers</td>
      <td>2016</td>
      <td>Google</td>
    </tr>
  </tbody>
</table>

## Notes

* List-Directed Input/Output: Comma-separated or space-separated values that looks like CSV.
* INI: Windows continues to make use of the INI specification today.
* SGML: Decendent of GML
* XML: inspired by GML
* JSON: Standardized in 2006
* XML: Recommended in 1999
* Protobufs: Open Sourced 2008
* Thrift: Open Sourced 2006
* MessagePack: Popular, since supported by over 40 programming languages.
* Smile: Can deserialize with fixed buffering
* Bond: inspired by Thrift/Protobufs, deprecated in 2025
* UBJSON: Binary format that is more human-readable. It uses printable ASCII in for field types.
* CBOR: design for internet of things where devices are memory and processor constrained.
* FlatBuffers: Table is an ordered sequence of aligned values prefixed with a pointer to a vTable structure that defines the layout of the Table.
* FlexBuffers: Can be used with FlatBuffers by storing a part of a serialized FlatBuffer in a FlexBuffer.

## References 

* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"