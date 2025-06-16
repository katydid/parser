# Comparison of Serialization Formats

<table border="1">
  <thead>
    <tr>
      <th>Format</th>
      <th>Schema</th>
      <th>Text/Binary</th>
      <th>Layout</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>GML</td>
      <td>No</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>List-Directed Input/Output or CSV</td>
      <td>No</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>INI</td>
      <td>No</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>ASN.1</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>SGML</td>
      <td>No</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Property List</td>
      <td>No</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>JSON</td>
      <td>Optional</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>XML</td>
      <td>Optional</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Binary Property List</td>
      <td>No</td>
      <td>Binary</td>
      <td>Pointer-based</td>
    </tr>
    <tr>
      <td>Protocol Buffers</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>YAML</td>
      <td>Optional</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Apache Thrift</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Message Pack</td>
      <td>No</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Apache Avro</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Binary JSON (BSON)</td>
      <td>No</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Smile</td>
      <td>No</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>Bond</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>UBJSON</td>
      <td>No</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>TOML</td>
      <td>No</td>
      <td>Text</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>CapnProto</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Pointer-based</td>
    </tr>
    <tr>
      <td>Apache Parquet</td>
      <td>No</td>
      <td>Binary</td>
      <td>Column-based</td>
    </tr>
    <tr>
      <td>CBOR</td>
      <td>No</td>
      <td>Binary</td>
      <td>Sequential</td>
    </tr>
    <tr>
      <td>FlatBuffers</td>
      <td>Yes</td>
      <td>Binary</td>
      <td>Pointer-based</td>
    </tr>
    <tr>
      <td>FlexBuffers</td>
      <td>No</td>
      <td>Binary</td>
      <td>Pointer-based</td>
    </tr>
  </tbody>
</table>

## References

* "A survey of json-compatible binary serialization specifications - Juan Cruz Viotti and Mital Kinderkhedia (2022)"