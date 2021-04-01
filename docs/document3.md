## Appendix Data Types (Normative)

This appendix defines the data types that a Resource can be defined to be.

<table>
    <caption>Data Types</caption>
    <thead>
        <tr>
            <th>Data Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>String</strong></td>
            <td>A UTF-8 string, the minimum and/or maximum length of the String MAY be defined.</td>
        </tr>
        <tr>
            <td><strong>Integer</strong></td>
            <td>An 8, 16, 32 or 64-bit signed integer. The valid range of the value for a Resource SHOULD be defined. This data type is also used for the purpose of enumeration.</td>
        </tr>
        <tr>
            <td><strong>Unsigned Integer</strong></td>
            <td>An 8, 16, 32 or 64-bit unsigned integer. The valid range of the value for a Resource SHOULD be defined. This data type may also used as a bitmask whereby bit positions range from 0 to sizeof(unsigned integer)-1. For example, an 8 bit unsigned integer can hold a bitmask of 8 "features" ranging from bit(0) to bit(7) whereby each bit position, when set, corresponds to the unsigned integer value 2^(bit position). The following example shows an 8-bit unsigned integer value illustrates a bitmask with "0001 0010" whereby bit(1) and bit(4) are set resulting in the unsigned integer value 18 (i.e., 2^1+2^4).</td>
        </tr>
        <tr>
            <td><strong>Float</strong></td>
            <td>A 32 or 64-bit floating point value. The valid range of the value for a Resource SHOULD be defined.</td>
        </tr>
        <tr>
            <td><strong>Boolean</strong></td>
            <td>An 8 bit unsigned integer with the value 0 for False and the value 1 for True.</td>
        </tr>
        <tr>
            <td><strong>Opaque</strong></td>
            <td>A sequence of binary octets, the minimum and/or maximum length of the String MAY be defined.</td>
        </tr>
        <tr>
            <td><strong>Time</strong></td>
            <td>Unix Time. A signed integer representing the number of seconds since Jan 1<sup>st</sup>, 1970 in the UTC time zone.</td>
        </tr>
        <tr>
            <td><strong>Objlnk</strong></td>
            <td><p>Object Link. The object link is used to refer to an Instance of a given Object.</p>
                <p>An Object Link referencing no Object Instance will contain 2 MAX-ID values (null link).</p></td>
        </tr>
        <tr>
            <td><strong>Corelnk</strong></td>
            <td><p>CoRE Link. A link is used to refer to Resources on a LWM2M Client and their attributes as specified in [RFC6690].</p></td>
        </tr>
        <tr>
            <td><strong>none</strong></td>
            <td>No specific data type affected to that resource: it exclusively concerns Executable Resource.</td>
        </tr>
    </tbody>
</table>
<table>
    <caption>Data Type Mapping</caption>
    <thead>
        <tr>
            <th>Data Type</th>
            <th>Text Format</th>
            <th>TLV Format</th>            
            <th>SenML JSON Format</th>
            <th>CBOR, LwM2M CBOR, and SenML CBOR Formats</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>String</strong></td>
            <td>Represented as a UTF-8 string.</td>
            <td>Represented as a UTF-8 string of Length bytes.</td>            
            <td>Represented as a string.</td>
            <td>Represented as a UTF-8 text string, as defined in Section 2 of [RFC7049].</td>
        </tr>
        <tr>
            <td><strong>Integer</strong></td> 
<td><p>Represented as an ASCII signed integer.</p>
                <p>For example, the integer value -750 results in the 4 characters/byte long ASCII string “-750”.</p></td>
            <td>Represented as a binary signed integer in network byte order, and in two’s complement representation. The value may be 1 (8-bit), 2 (16-bit), 4 (32-bit) or 8 (64-bit) bytes long as indicated by the Length field. When transmitted over network, the data is represented in network byte order (big endian).</td>            
            <td>Represented as a number.</td>
            <td>Represented as an integer, as defined in Section 2 of [RFC7049].</td>            
        </tr>
        <tr>
            <td><strong>Unsigned Integer</strong></td>
<td><p>Represented as an ASCII unsigned integer.</p>
                <p>For example, the unsigned integer value 18 results in a 2 character/byte long ASCII string “18”.</p></td>
            <td>Represented as a binary unsigned integer in network byte order. The value may be 1 (8-bit), 2 (16-bit), 4 (32-bit) or 8 (64-bit) bytes long as indicated by the Length field. When transmitted over network, the data is represented in network byte order (big endian).</td>            
            <td>Represented as a number.</td>
            <td>Represented as an unsigned integer, as defined in Section 2 of [RFC7049].</td>   
        </tr>
        <tr>
            <td><strong>Float</strong></td>
<td><p>Represented as an ASCII signed numeric representation.</p>
                <p>For example, we use a floating point number with the significand of 6.667, a base of 10 and the exponent of -11. This represents the number 6.667e-11 in scientific notation and will be represented as &quot;0.00000000006667&quot; as an ASCII string.</p></td>
            <td>Represented as a binary floating point value [FLOAT]. The value may use the binary32 (4 byte length) or binary64 (8 byte length) format as indicated by the Length field. When transmitted over network, the data is represented in network byte order (big endian).</td>            
            <td>Represented as a number.</td>
            <td>Represented as a floating-point number, as defined in Section 2 and Section 2.3 of [RFC7049].</td>   
        </tr>
        <tr>
            <td><strong>Boolean</strong></td>
 <td>Represented as the ASCII value 0 or 1.</td>
            <td>Represented as an 8 bit unsigned Integer with value 0, or 1. The Length of a Boolean value MUST always be 1 byte.</td>            
            <td>Represented as the JSON boolean data type, which is either represented as the string 'true' or 'false'. </td>
            <td>Represented as the value 'True' or 'False', as defined in Table 2 of [RFC7049].</td>   
        </tr>
        <tr>
            <td><strong>Opaque</strong></td>
<td><p>Represented as a Base64 encoding of the binary data [RFC4648].</p>
                <p>For example, the sequence of bytes (in hex notation) {0x01, 0x02, 0x03, 0x04, 0x05} converts to the ASCII string “AQIDBAU=” in Base64 encoding.</p></td>
            <td>Represented as a sequence of binary data of Length bytes.</td>            
            <td>Represented as a URL-safe Base64 encoded representation of the data with padding omitted in a JSON string, as defined in Section 4.3 of [SENML].</td>
            <td>Represented as a byte string, as defined in Section 2 of [RFC7049].</td>   
        </tr>
        <tr>
            <td><strong>Time</strong></td>
<td>Represented as an ASCII integer.<br />
                For example, 1476186613 seconds since Jan 01 1970, which represents Tuesday, 11-Oct-16 11:50:13 UTC, are represented as the ASCII string &quot;1476186613&quot;, which has 10 characters/bytes.</td>
            <td>Same representation as Integer.</td>            
            <td>Represented as a number.</td>
            <td>Represented as an unsigned integer or a date/time string, as defined in Section 2.4.1 of [RFC7049].</td>
        </tr>
        <tr>
            <td><strong>Objlnk</strong></td>
                <p>An Object Link referencing no Object Instance will contain 2 MAX-ID values (null link).</p></td>
            <td>Represented as a UTF-8 string containing 2 16-bit ASCII integers separated by a ‘:’ ASCII character. The first one represents the Object ID, and the second one represents the Object Instance ID.</td>
            <td>Represented as two concatenated 16 bit unsigned integers following the Network Byte Order convention. The first one represents the Object ID, and the second one represents the Object Instance ID. This value is always 4 bytes long.</td>            
            <td>Represented as a string containing two 16-bit ASCII integers separated by a ':' ASCII character. 
                The first one represents the Object ID, and the second one represents the Object Instance ID.</td>
            <td>Represented as a string containing two 16-bit ASCII integers separated by a ':' ASCII character. 
                The first one represents the Object ID, and the second one represents the Object Instance ID.</td>   
        </tr>
        <tr>
            <td><strong>Corelnk</strong></td>
            <td>Represented as a String using CoRE Link format. For example, an IPSO temperature sensor with measurements query for a resource, with a resource attribute greater than 23: </3303/0/5700>;gt=23 If the Corelnk refers to an Instance of a given Object (as an Objlnk), then the same validity check as with Objlnk is required.</td>
            <td>Same representation as String.</td>            
            <td>Represented as a string using the CoRE Link format.</td>
            <td>Represented as a UTF-8 text string, as defined in Section 2 of [RFC7049].</td>
        </tr>
        <tr>
            <td><strong>none</strong></td>
            <td>Not applicable</td>
            <td>Not applicable</td>            
            <td>The value is either represented as a string 'null' or as an empty field.</td>
            <td>Represented as the value 'Null', as defined in Table 2 of [RFC7049].</td>   
        </tr>
    </tbody>
</table>



<figure class="text-center">
      <img src="images/object_link_resource_simple_illustration.svg" alt="Object link Resource simple illustration">
      <figcaption>Object link Resource simple illustration</figcaption>
</figure>

