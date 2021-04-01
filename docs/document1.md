## Scope

This document, the LwM2M CORE technical specification, describes the LwM2M messaging layer. The LwM2M TRANSPORT specification \[LwM2M-TRANSPORT]\, a companion specification, details the mapping of the messaging layer to selected transports. The separation between transport and messaging layer improves readability and simplifies extending LwM2M to further transports. The LwM2M messaging layer uses a RESTful design with several interfaces and a simple data model.  

### LwM2M version 1.2

This specification defines version 1.2 of the LwM2M protocol and augments \[LwM2M-TS\_1.1\]. Version 1.2 is backwards compatible to LwM2M version v1.0 and v1.1 with respect to mandatory features. 

LwM2M v1.2 adds the following new features:  

* New transports for LwM2M; this allows LwM2M messaging to be conveyed over MQTT and over HTTP. 
* Optimizations for the bootstrapping interface; this reduces the amount of data and the number of messages transmitted during the bootstrapping exchange.
* Optimizations for the registration interface; this reduces the amount of data transmitted during registration exchanges.
* Optimizations for the information reporting interface; observation attributes may now be included in an Observe operation.
* Support for LwM2M gateway functionality; this allows non-LwM2M IoT devices as well as LwM2M devices behind a gateway to be connected to the LwM2M ecosystem and to manage those devices remotely.
* New, highly optimized encoding format based on CBOR called LwM2M CBOR. 
* Enhanced functionality for firmware updates. 
* Definition of new notification attributes (edge, confirmable notification, and maximum historical queue). Edge allows notifications to be triggered on rising and falling edges. Confirmable notifications allow the control of reliable transmissions of notifications. Maximum historical queue allows the control of time-series data usage. 
* Clarifications of object versioning rules. 
* Updates to use the latest communication security protocols based on TLS and DTLS 1.3 (as well as the use of the Connection ID).
* Flexibility to control the use of TLS and DTLS 1.3 through configuration information.
* Untangling the relationship of security credentials and their server configuration.

There also numerous clarifications and editorial improvements as well as additional examples based on feedbacks received from the LwM2M development community.

Details about the transport bindings can be found in \[LwM2M-TRANSPORT\].

### LwM2M version 1.1

LwM2M v1.1 added the following features to v1.0: 

* Enhancement of the LwM2M bootstrapping capabilities allowing for incremental upgrades.  

* Improved support for Public Key Infrastructure (PKI) deployments. 

* Introduction of enhanced registration sequence mechanisms by the LwM2M Client to LwM2M Server(s).

* Support for LwM2M over TCP/TLS to better support firewall and NAT traversal. 

* Support for application layer security for LwM2M based on OSCORE.

* Better support of LwM2M over Low Power WANs, including 3GPP CIoT & LoRaWAN.

* Extended LwM2M operations to enable Resource Instance level access.

* Performance improvement for retrieving and updating Resources of multiple objects.

* Support for JSON using SenML with CBOR serialization for compressed payload with highly efficient transmission.

* Addition of new data types.

### LwM2M version 1.0

LwM2M v1.0 offers the following features:

-   Simple resource model with the core set of objects and resources defined in this specification. The full list of registered objects can be found at [OMNA](http://www.openmobilealliance.org/wp/OMNA/LwM2M/LwM2MRegistry.html).

-   Operations for creation, update, deletion, and retrieval of resources.

-   Asynchronous notifications of resource changes.

-   Support for several serialization formats, namely TLV, JSON, Plain Text and binary data formats and the core set of LightweightM2M Objects.

-   UDP and SMS transport support.

-   Communication security based on the DTLS protocol supporting different types of credentials.

-   Queue Mode offers functionality for an LwM2M Client to inform the LwM2M Server that it may be disconnected for an extended period and when it becomes reachable again.

-   Support for use of multiple LwM2M Servers.

-   Provisioning of security credentials and access control lists by a dedicated LwM2M bootstrap-server.

## References

### Normative References

<table>
    <caption>Normative References</caption>
    <tbody>
        <tr>
          <td><strong>[LwM2M-TRANSPORT]</strong></td>
          <td>Open Mobile Alliance, "Lightweight Machine to Machine Technical Specification: Transport Layer"</td>
        </tr>
        <tr>
          <td><strong>[LwM2M-TS_1.0]</strong></td>
          <td>Open Mobile Alliance, "Lightweight Machine to Machine Technical Specification, Version 1.0.2", February 2018</td>
        </tr>
        <tr>
          <td><strong>[LwM2M-TS_1.1]</strong></td>
          <td>Open Mobile Alliance, "Lightweight Machine to Machine Technical Specification, Version 1.1.1", June 2019</td>
        </tr>
        <tr>
           <td><strong>[DMREPPRO]</strong></td>
            <td>"OMA Device Management Representation Protocol, Version 1.3", Open Mobile Alliance™, <br>
                 OMA-TS-DM_RepPro-V1_3, <a href="http://www.openmobilealliance.org">URL:http://www.openmobilealliance.org/</a></td>
        </tr>
        <tr>
            <td><strong>[OMADICT]</strong></td>
            <td>"Dictionary for OMA Specifications", Open Mobile Alliance™,<br>
                OMA-ORG-Dictionary-V2_9, <a href="http://www.openmobilealliance.org/">URL:http://www.openmobilealliance.org/</a></td>
        </tr>
        <tr>
            <td><strong>[OMNA]</strong></td>
            <td>"OMNA Lightweight M2M (LwM2M) Object &amp; Resource Registry", <a href="http://www.openmobilealliance.org/"><em>URL:http://www.openmobilealliance.org/</em></a></td>	
        </tr>
        <tr>
            <td><strong>[3GPP 23.003]</strong></td>
            <td>3GPP TS 23.003 "Numbering, addressing and identification"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 23.032]</strong></td>
            <td>3GPP TS 23.032 "Universal Geographical Area Description (GAD)"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 23.401]</strong></td>
            <td>3GPP TS 23.401 "General Packet Radio Service (GPRS) enhancements for Evolved Universal Terrestrial Radio Access Network (E-UTRAN) access"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 24.008]</strong></td>
            <td>3GPP TS 24.008 "Mobile radio interface Layer 3 specification; Core network protocols; Stage 3"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 25.331]</strong></td>
            <td>3GPP TS 25.331 “Radio Resource Control (RRC); Protocol specification”</td>
        </tr>
        <tr>
            <td><strong>[3GPP 31.115]</strong></td>
            <td>3GPP TS 31.115 "Secured packet structure for (Universal) Subscriber Identity Module (U)SIM Toolkit applications"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 31.116]</strong></td>
            <td>3GPP TS 31.116 "Remote APDU Structure for (U)SIM Toolkit applications"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 36.133]</strong></td>
            <td>3GPP TS 36.133 "Evolved Universal Terrestrial Radio Access (E-UTRA); Requirements for support of radio resource management"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 36.214]</strong></td>
            <td>3GPP TS 36.214 "Evolved Universal Terrestrial Radio Access (E-UTRA); Physical layer; Measurements"</td>
        </tr>
        <tr>
            <td><strong>[3GPP 44.018]</strong></td>
            <td>3GPP TS 44.018 "Mobile radio interface layer 3 specification; GSM/EDGE Radio Resource Control (RRC) protocol"</td>
        </tr>
        <tr>
            <td><strong>[3GPP2 C.S0078-0]</strong></td>
            <td>3GPP2 C.S0078-0 (V1.0): "Secured packet structure for CDMA Card Application Toolkit (CCAT) applications"</td>
        </tr>
        <tr>
            <td><strong>[3GPP2 C.S0079-0]</strong></td>
            <td>3GPP2 C.S0079-0 (V1.0) "Remote APDU Structure for CDMA Card Application Toolkit (CCAT) applications"</td>
        </tr>
        <tr> 		
           <td><strong>[ETSI 102 221]</strong></td>
            <td>ETSI TS 102 221 "Smart Cards; UICC-Terminal interface; Physical and logical characteristics", <a href="http://www.etsi.org/">URL:http://www.etsi.org/</a></td>
        </tr>
        <tr>
            <td><strong>[ETSI 102 223]</strong></td>
            <td>ETSI TS 102 223 "Smart Cards; Card Applications Toolkit (CAT)", <a href="http://www.etsi.org/">URL:http://www.etsi.org/</a></td>
        </tr>
        <tr>
            <td><strong>[ETSI 102 225]</strong></td>
            <td>ETSI TS 102 225 "Smart Cards; Secured packet structure for UICC based applications", <a href="http://www.etsi.org/">URL:http://www.etsi.org/</a></td>
        </tr>
        <tr>
            <td><strong>[ETSI 102 226]</strong></td>
            <td>ETSI TS 102 226 "Smart cards; Remote APDU structure for UICC based applications", <a href="http://www.etsi.org/">URL:http://www.etsi.org/</a></td>
        </tr>
        <tr>
           <td><strong>[CoAP]</strong></td>
            <td>Z. Shelby, K. Hartke, C. Bormann, B. Frank, "The Constrained Application Protocol (CoAP)", June 2014, <a href="http://www.ietf.org/rfc/rfc7252.txt">URL:http://www.ietf.org/rfc/rfc7252.txt</a></td>
        </tr>
        <tr>
           <td><strong>[CoAP_Blockwise]</strong></td>
            <td>C. Bormann, Z. Shelby, "Block-wise transfers in CoAP", August 2016, <a href="http://www.ietf.org/rfc/rfc7959.txt">URL:http://www.ietf.org/rfc/rfc7959.txt</a></td>
        </tr>
        <tr>
            <td><strong>[DynLink]</strong></td>
            <td>M. Koster, B. Silverajan, Ed., "Dynamic Resource Linking for Constrained RESTful Environments", (work in progress) <a href="https://tools.ietf.org/html/draft-ietf-core-dynlink-11">draft-ietf-core-dynlink-11</a>, July 2020</td>
        </tr>
       	<tr>
            <td><strong>[FLOAT]</strong></td>
            <td>ANSI/IEEE Std 754-2019, “IEEE Standard for Floating-Point Arithmetic”,  IEEE Microprocessor Standards Committee, July 2019</td>
        </tr>
        <tr>
           <td><strong>[GLOBALPLATFORM]</strong></td>
            <td>GlobalPlatform Card Specification V2.3.1 (GPC_SPE_034), <a href="http://www.globalplatform.org/">URL:http://www.globalplatform.org/</a></td></td>
        </tr>
        <tr>
           <td><strong>[GP AMD_A]</strong></td>
            <td>Updated GlobalPlatform Reference needed</td>
        </tr>
        <tr>
           <td><strong>[GP SCP03]</strong></td>
            <td>GlobalPlatform Secure Channel Protocol 03 (SCP 03) Amendment D v1.1 Sept 2009</td>
        </tr>
        <tr>
            <td><strong>[OSCORE]</strong></td>
            <td>G. Selander, J. Mattsson, F. Palombini, L. Seitz, "Object Security for Constrained RESTful Environments (OSCORE)", July 2019, <a href="https://tools.ietf.org/html/rfc8613">https://www.rfc-editor.org/rfc/rfc8259.html</a></td>
        </tr>
        <tr>
	    <td><strong>[PKCS#15]</strong></td>
            <td>"PKCS #15 v1.1: Cryptographic Token Information Syntax Standard", RSA Laboratories, June 6, 2000,		   	    
		    <a href="URL:ftp://ftp.cert.dfn.de/pub/pca/docs/PKCS/ftp.rsa.com/pkcs-15/pkcs-15v1_1.pdf">URL:ftp://ftp.cert.dfn.de/pub/pca/docs/PKCS/ftp.rsa.com/pkcs-15/pkcs-15v1_1.pdf</a></td>
        </tr>
        <tr>  
	    <td><strong>[SENML]</strong></td>
            <td>C. Jennings, Z. Shelby, J. Arkko, A. Keranen, C. Bormann, "Sensor Measurement Lists (SenML)", July 2018, <a href="https://tools.ietf.org/html/rfc8428.txt">URL:https://tools.ietf.org/html/rfc8428.txt</a></td>
        </tr>
	<tr>
            <td><strong>[TR-069]</strong></td>
            <td>Broadband Forum: "TR-069 CPE WAN Management Protocol" Issue: 1 Amendment 5", <a href="URL:http://www.broadband-forum.org/technical/download/TR-069_Amendment-5.pdf">URL:http://www.broadband-forum.org/technical/download/TR-069_Amendment-5.pdf</a></td> 
	</tr>
	<tr>
           <td><strong>[WGS84]</strong></td>
            <td>World Geodetic System 1984 (WGS 84), <a href="URL:https://earth-info.nga.mil/GandG/update/index.php?dir=wgs84&action=wgs84">URL:https://earth-info.nga.mil/GandG/update/index.php?dir=wgs84&action=wgs84</a></td> 
        </tr>
        <tr>	
           <td><strong>[RFC2119]</strong></td>
            <td>S. Bradner, "Key words for use in RFCs to Indicate Requirement Levels", March 1997,<a  href="http://www.ietf.org/rfc/rfc2119.txt">URL:http://www.ietf.org/rfc/rfc2119.txt</a></td>
        </tr>
        <tr>
           <td><strong>[RFC3986]</strong></td>
            <td>T. Berners-Lee, R. Fielding, L. Masinter, "Uniform Resource Identifier (URI): Generic Syntax", January 2005<a href="http://www.ietf.org/rfc/rfc3986.txt">URL:http://www.ietf.org/rfc/rfc3986.txt</a></td>
        </tr>
        <tr>
            <td><strong>[RFC4122]</strong></td>
            <td>P. Leach, M. Mealling, R. Salz, "A Universally Unique Identifier (UUID) URN Namespace", July 2005,<a href="http://www.ietf.org/rfc/rfc4122.txt">URL:http://www.ietf.org/rfc/rfc4122.txt</a></td>
        </tr>
        <tr>
            <td><strong>[RFC4648]</strong></td>
            <td>P. S. Josefsson, “The Base16, Base32, and Base64 Data Encodings”, October 2006,<a href="http://www.ietf.org/rfc/rfc4648.txt">URL:http://www.ietf.org/rfc/rfc4648.txt</a></td>
        </tr>
        <tr>
           <td><strong>[RFC6234]</strong></td>
            <td>D. Eastlake 3rd, T. Hansen, “US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF)”, May 2011,<a href="http://www.ietf.org/rfc/rfc6234.txt">URL:http://www.ietf.org/rfc/rfc6234.txt</a></td>
        </tr>
        <tr>			
            <td><strong>[RFC6690]</strong></td>
            <td>Shelby, Z. "Constrained RESTful Environments (CoRE) Link Format", August 2012, <a href="http://www.ietf.org/rfc/rfc6690.txt">URL:http://www.ietf.org/rfc/rfc6690.txt</a></td>
        </tr>
        <tr>
            <td><strong>[RFC6920]</strong></td>
            <td>S. Farrell, D. Kutscher, C. Dannewitz, B. Ohlman, A. Keranen, P. Hallam-Baker, "Naming Things with Hashes", April 2013, <a href="https://tools.ietf.org/rfc/rfc6920.txt">URL:https://tools.ietf.org/rfc/rfc6920.txt</a></td>
        </tr>
	<tr>
             <td><strong>[RFC7542]</strong></td>
            <td>A. DeKok, "The Network Access Identifier", May 2015,<a href="https://tools.ietf.org/html/rfc7542.txt">URL:https://tools.ietf.org/html/rfc7542.txt</a></td>
        </tr>
        <tr>
             <td><strong>[RFC7049]</strong></td>
            <td>AC. Bormann, P. Hoffman, "Concise Binary Object Representation (CBOR)", October 2013,<a href="https://tools.ietf.org/rfc/rfc7049.txt">URL:https://tools.ietf.org/rfc/rfc7049.txt</a></td>
	</tr>
        <tr>
              <td><strong>[RFC7542]</strong></td>
            <td>A. DeKok, "The Network Access Identifier", May 2015,<a href="https://tools.ietf.org/rfc/rfc7542.txt">URL:https://tools.ietf.org/rfc/rfc7542.txt</a></td>
	</tr>
        <tr> 
           <td><strong>[RFC8790]</strong></td>
            <td>A. Keränen, M. Mohajer, "FETCH and PATCH with Sensor Measurement Lists (SenML)", June 2020, <a href="https://tools.ietf.org/rfc/rfc8790.txt">URL:https://tools.ietf.org/rfc/rfc8790.txt</a></td>
	</tr>
</td>
        </tr>
     </tbody>
</table>

{:page-break}

### Informative References

<table>
    <caption>Informative References</caption>
    <tbody>
        <tr>
           <td><strong>[3GPP 23.682]</strong></td>
           <td>3GPP TS 23.682 "Architecture enhancements to facilitate communications with packet data networks and applications"</td>
        </tr>
        <tr>
           <td><strong>[3GPP 23.720]</strong></td>
           <td>3GPP TR 23.720 "Study on architecture enhancements for Cellular Internet of Things"</td>
        </tr>
        <tr>
           <td><strong>[3GPP 24.301]</strong></td>
           <td>3GPP TS 24.301 "Non-Access-Stratum (NAS) protocol for Evolved Packet System (EPS); Stage 3"</td>
        </tr>
        <tr>
          <td><strong>[3GPP 27.060]</strong></td>
            <td>3GPP TS 27.060 "Packet domain; Mobile Station (MS) supporting Packet Switched services"</td>
        </tr>
        <tr>
           <td><strong>[3GPP 29.061]</strong></td>
           <td>3GPP TS 29.061 "Interworking between the Public Land Mobile Network (PLMN) supporting packet based services and Packet Data Networks (PDN)"</td>
        </tr>
        <tr>
           <td><strong>[3GPP 31.102]</strong></td>
           <td>3GPP TS 31.102 "Characteristics of the Universal Subscriber Identity Module (USIM) application"</td>
        </tr>
        <tr>
             <td><strong>[RFC7459]</strong></td>
            <td>M. Thomson, J. Winterbottom, "Representation of Uncertainty and Confidence in the Presence Information Data Format Location Object (PIDF-LO)", February 2015, <a href="https://tools.ietf.org/html/rfc7459">URL:https://tools.ietf.org/html/rfc7459</a></td>
        </tr>
    </tbody>
</table>


## Terminology and Conventions

### Conventions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in \[RFC2119\].

All sections and appendixes, except "Scope" and "Introduction", are normative, unless they are explicitly indicated to be informative.

### Definitions

<table>
    <caption>Definitions</caption>
     <tr>
        <td><strong>Object</strong></td>
        <td>An Object is a collection of logically related resources.</td>
    </tr>
        <tr>
        <td><strong>Object Instance</strong></td>
        <td>An Object Instance is one occurrence of an Object.</td>
    </tr>
        <tr>
        <td><strong>Resource</strong></td>
        <td>A Resource is an atomic unit of information.</td>
    </tr>
        <tr>
        <td><strong>Resource Instance</strong></td>
        <td>A Resource Instance is one occurrence of a Resource.</td>
    </tr>
    <tr>
        <td><strong>LwM2M Client</strong></td>
        <td>Component running on a device implementing the LwM2M protocol for interacting with the LwM2M Server and the LwM2M Bootstrap-Server. LwM2M Clients are often implemented in IoT devices and gateways. </td>
    </tr>    
    <tr>
        <td><strong>LwM2M Server</strong></td>
        <td>Component implementing the server-side functionality of the LwM2M protocol for interacting with an LwM2M Client. Typically, the LwM2M Server software is running on a non-IoT device, such as an on-premise server or in a cloud-based infrastructure. </td>
    </tr>
    <tr>
        <td><strong>LwM2M Bootstrap-Server</strong></td>
        <td>The LwM2M Bootstrap-Server is a server responsible for provisioning essential information, including credentials, into the LwM2M Client to enable the LwM2M Client to perform the "Register" operation with one or more LwM2M Servers. Very often, the LwM2M Bootstrap-Server is the first LwM2M entity an LwM2M Client interacts with. The Bootstrap Interface is the only interface used between the LwM2M Client and the LwM2M Bootstrap-Server.</td>
    </tr>
    <tr>
        <td><strong>LwM2M Bootstrap-Server Account</strong></td>
        <td> LwM2M Security Object Instance with Bootstrap-Server Resource true </td>
    </tr>
    <tr>
        <td><strong>LwM2M Server Account</strong></td> 
        <td> LwM2M Security Object Instance with Bootstrap-Server Resource false and associated LwM2M Server Object Instance </td>
    </tr> 
    <tr>
        <td><strong>LwM2M Registration Session</strong></td> 
        <td>An LwM2M Registration Session is an association between an LwM2M Client and an LwM2M Server. It starts with the successful LwM2M register operation and ends when the registration lifetime expires, with a successful LwM2M de-register operation or when an error is detected. </td>
    </tr>
    <tr>
        <td><strong>LwM2M Bootstrap Session</strong></td> 
        <td>An LwM2M Bootstrap Session is an association between an LwM2M Client and an LwM2M Bootstrap-Server. It starts with the successful Bootstrap-Request or Bootstrap-Pack-Request operation and ends respectively with the Bootstrap-Finish or Bootstrap-Pack operation or when an error is detected.</td>
    </tr>
    <tr>
        <td><strong>Transport Session</strong></td> 
        <td>A Transport Session is application-independent association between the LwM2M Client and LwM2M Server or LwM2M Bootstrap-Server to enable application layer communications.</td>
    </tr> 		
</table>

Note that wherever there is an LwM2M Security Object Instance there is potentially an associated LwM2M OSCORE Object Instance. Kindly consult \[OMADICT\](http://openmobilealliance.org/documents/dictionary/OMA-ORG-Dictionary-V2_9-20120626-A.pdf) for more definitions used in this document.

### Abbreviations

<table>
    <caption>Abbreviations</caption>
        <tbody>
	    <tr>
                <td><strong>3GPP</strong></td>
                <td>3rd Generation Partnership Project</td>
	    </tr>
            <tr>
                <td><strong>AID</strong></td>
                <td>Application Identifier</td>
	    </tr>
            <tr>
                <td><strong>ABNF</strong></td>
                <td>Augmented Backus-Naur Form </td>
	    </tr>
            <tr>
                <td><strong>ACL</strong></td>
                <td>Access Control List</td>
	    </tr>
            <tr>
                <td><strong>AEAD</strong></td>
                <td>Authenticated Encryption with Additional Data</td>
	    </tr>
            <tr>
                <td><strong>AES</strong></td>
                <td>Advanced Encryption Standard</td>
	    </tr>
            <tr>
                <td><strong>APN</strong></td>
                <td>APN Access Point Name</td>
	    </tr>
            <tr>
               <td><strong>ASCII</strong></td>
                <td>American Standard Code for Information Interchange</td>
	    </tr>
            <tr>
               <td><strong>ASN.1</strong></td>
                <td>Abstract Syntax Notation #1</td>
	    </tr>
            <tr>
               <td><strong>CA</strong></td>
                <td>Certification Authority</td>
	    </tr>
            <tr>
                <td><strong>CBOR</strong></td>
                <td>CBOR Concise Binary Object Representation</td>
	    </tr>
            <tr>
                <td><strong>CDMA</strong></td>
                <td>CDMA Code Division Multiple Access</td>
	    </tr>
            <tr>
                <td><strong>CIoT</strong></td>
                <td>CIoT Cellular Internet of Things</td>
	    </tr>
            <tr>		    
                <td><strong>CoAP</strong></td>
                <td>Constrained Application Protocol</td>
            </tr>
            <tr>
                <td><strong>CoRE</strong></td>
                <td>Constrained RESTful Environments</td>
            </tr>
            <tr>
                <td><strong>COSE</strong></td>
                <td>CBOR Object Signing and Encryption</td>
            </tr>
            <tr>
                <td><strong>CRS</strong></td>
                <td>Coordinate Reference Systems</td>
            </tr>
            <tr>
                <td><strong>DF</strong></td>
                <td>Dedicated File</td>
            </tr>
            <tr>
                <td><strong>DER</strong></td>
                <td>Distinguished Encoding Rules</td>
            </tr>
            <tr>
                <td><strong>DIR</strong></td>
                <td>Directory File</td>
            </tr>
            <tr>
                <td><strong>DO</strong></td>
                <td>Data Object</td>
            </tr>
            <tr>
                <td><strong>DODF</strong></td>
                <td>Data Object Directory File</td>
            </tr>
            <tr>
                <td><strong>DSL</strong></td>
                <td>Digital Subscriber Line</td>
            </tr>
            <tr>	    
                <td><strong>DTLS</strong></td>
                <td>Datagram Transport Layer Security</td>
            </tr>
	     <tr>
                <td><strong>EDGE</strong></td>
                <td>Enhanced Data rates for GSM Evolution</td>
            </tr>
	     <tr>
                <td><strong>EF</strong></td>
                <td>Elementary File</td>
            </tr>
	     <tr>
                <td><strong>ESN</strong></td>
                <td>Electronic Serial Number</td>
            </tr>
	     <tr>
                <td><strong>EST</strong></td>
                <td>Enrollment over Secure Transport</td>
            </tr>
	     <tr>
                <td><strong>FDD</strong></td>
                <td>Frequency Division Duplex</td>
            </tr>
	     <tr>
                <td><strong>GSM</strong></td>
                <td>Global System for Mobile</td>
            </tr>
	     <tr>
                <td><strong>HKDF</strong></td>
                <td>MAC-based Key Derivation Function</td>
            </tr>
	     <tr>
                <td><strong>HMAC</strong></td>
                <td>Hashed Message Authentication Code</td>
            </tr>
	     <tr>
                <td><strong>HTTP</strong></td>
                <td>Hypertext Transfer Protocol</td>
            </tr>
	     <tr>
                <td><strong>HTTPS</strong></td>
                <td>HTTP Secure</td>
            </tr>
	     <tr>
                <td><strong>IANA</strong></td>
                <td>Internet Assigned Numbers Authority</td>
            </tr>
	     <tr>
                <td><strong>ID</strong></td>
                <td>Identity/Identifier</td>
            </tr>
	     <tr>
                <td><strong>IE</strong></td>
                <td>Information(al) Element</td>
            </tr>
	     <tr>
                <td><strong>IEEE</strong></td>
                <td>Institute of Electrical and Electronic Engineers</td>
            </tr>
	     <tr>
                <td><strong>IMEI</strong></td>
                <td>International Mobile Equipment Identity</td>
            </tr>
	     <tr>
                <td><strong>IMSI</strong></td>
                <td>International Mobile Subscriber Identity</td>
            </tr>
	     <tr>
                <td><strong>IP</strong></td>
                <td>Internet Protocol</td>
            </tr>
	     <tr>
                <td><strong>IPSO</strong></td>
                <td>Internet Protocol for Smart Objects</td>
            </tr>
	     <tr>
                <td><strong>ISDN</strong></td>
                <td>Integrated Services Digital Network</td>
            </tr>
	     <tr>
                <td><strong>JOSE</strong></td>
                <td>Javascript Object Signing and Encryption </td>
            </tr>
	     <tr>
                <td><strong>JSON</strong></td>
                <td>JavaScript Object Notation</td>
            </tr>
	     <tr>     
              <td><strong>kB</strong></td>
              <td>Kilobyte; one kilobyte is 1000 bytes</td>
	    </tr>
            <tr>
              <td><strong>KiB</strong></td>
              <td>Kibibyte; one kibibyte is 1024 bytes</td>
	    </tr>
            <tr>
              <td><strong>KIc</strong></td>
              <td>Key and algorithm Identifier for ciphering</td>
	    </tr>
            <tr>
              <td><strong>kID</strong></td>
              <td>Key and algorithm IDentifier</td>
	    </tr>
            <tr>
              <td><strong>LAC</strong></td>
              <td>Location Area Code</td>
	    </tr>
            <tr>
             <td><strong>LoRaWAN</strong></td>
             <td>LOng RAnge Wide Area Network</td>
            </tr>
            <tr>
             <td><strong>LQI</strong></td>
             <td>Link Quality Indicator</td>
            </tr>
            <tr>
             <td><strong>LSB</strong></td>
             <td>LSB Least Significant Bit</td>
            </tr>
            <tr>
             <td><strong>LTE</strong></td>
             <td>Long Term Evolution</td>
            </tr>
            <tr>
             <td><strong>LwM2M</strong></td>
             <td>Lightweight M2M</td>
            </tr>
            <tr>
             <td><strong>M2M</strong></td>
             <td>Machine to Machine</td>
            </tr>
            <tr>
             <td><strong>MEID</strong></td>
             <td>Mobile Equipment Identifier</td>
            </tr>
            <tr>
             <td><strong>MQTT</strong></td>
             <td>Message Queuing Telemetry Transport</td>
            </tr>
            <tr>
             <td><strong>MSISDN</strong></td>
             <td>Mobile Subscriber ISDN Number</td>
            </tr>
            <tr>
             <td><strong>MSB</strong></td>
             <td>Most Significant Bit</td>
            </tr>
            <tr>
             <td><strong>NAI</strong></td>
             <td>Network Access Identifier</td>
            </tr>
            <tr>	     
                <td><strong>NB-IoT</strong></td>
                <td>NarrowBand Internet of Things</td>
            </tr>
	    <tr>
                <td><strong>NRSRQ</strong></td>
                <td>Narrowband Reference Signal Received Quality</td>
            </tr>
	     <tr>		    
                <td><strong>OCSP</strong></td>
                <td>Online Certificate Status Protocol</td>
            </tr>
	     <tr>
               <td><strong>ODF</strong></td>
                <td>Object Directory File</td>
            </tr>
	     <tr>
               <td><strong>OID</strong></td>
                <td>Object ID</td>
            </tr>
	     <tr>	     
                <td><strong>OMNA</strong></td>
                <td>Open Mobile Naming Authority</td>
            </tr>
	     <tr>
                <td><strong>OSCORE</strong></td>
                <td>Object Security for Constrained RESTful Environments</td>
            </tr>
	     <tr>
                <td><strong>PDN</strong></td>
                <td>Packet Data Network</td>
            </tr>
	     <tr>
                <td><strong>PDU</strong></td>
                <td>Protocol Data Unit Data Network</td>
            </tr>
	     <tr>
                <td><strong>PFS</strong></td>
                <td>Perfect Forward Secrecy</td>
            </tr>
	     <tr>
                <td><strong>PIX</strong></td>
                <td>Proprietary application Identifier eXtension</td>
            </tr>
	     <tr>
                <td><strong>PKI</strong></td>
                <td>Public Key Infrastructure</td>
            </tr>
	     <tr>	     
                <td><strong>PKCS</strong></td>
                <td>Public Key Cryptography Standard</td>
            </tr>
	     <tr>
                <td><strong>PLC</strong></td>
                <td>Power Line Communications</td>
            </tr>
	     <tr>
                <td><strong>PSK</strong></td>
                <td>Pre-Shared Key</td>
            </tr>
	     <tr>
                <td><strong>RID</strong></td>
                <td>Registered application provider IDentifier</td>
            </tr>
	     <tr>
                <td><strong>RDS</strong></td>
                <td>Reliable Data Service</td>
            </tr>
	     <tr>
                <td><strong>RPK</strong></td>
                <td>Raw Public Key</td>
            </tr>
	     <tr>
                <td><strong>RSCP</strong></td>
                <td>Received Signal Code Power</td>
            </tr>
	     <tr>
                <td><strong>RSRP</strong></td>
                <td>Reference Signal Received Power</td>
            </tr>
	     <tr>
                <td><strong>RSRQ</strong></td>
                <td>Reference Signal Received Quality</td>
            </tr>
	     <tr>
                <td><strong>RSSI</strong></td>
                <td>Received Signal Strength Indicator</td>
            </tr>
	     <tr>
                <td><strong>RTT</strong></td>
                <td>Round Trip Time</td>
            </tr>
	     <tr>
                <td><strong>RX</strong></td>
                <td>Receive</td>
            </tr>
	     <tr>
                <td><strong>SCEF</strong></td>
                <td>Service Capability Exposure Function</td>
            </tr>
	     <tr>
                <td><strong>SCR</strong></td>
                <td>Static Conformance Requirements</td>
            </tr>
	     <tr>
                <td><strong>SenML</strong></td>
                <td>Sensor Measurement Lists</td>
            </tr>
	     <tr>
                <td><strong>SHA</strong></td>
                <td>Secure Hask Algorithm</td>
            </tr>
	     <tr>
                <td><strong>SINR</strong></td>
                <td>Signal to Interference plus Noise Ratio</td>
            </tr>
	     <tr>
                <td><strong>SMCC</strong></td>
                <td>Serving Mobile Country Code</td>
            </tr>
	     <tr>
                <td><strong>SMNC</strong></td>
                <td>Serving Mobile Network Code</td>
            </tr>
	     <tr>		     
                <td><strong>SMS</strong></td>
                <td>Short Message Service</td>
            </tr>
	    <tr>
                <td><strong>SNI</strong></td>
                <td>Server Name Indication</td>
            </tr>
            <tr>
                <td><strong>SPI</strong></td>
                <td>Security Parameters Indication</td>
            </tr>
            <tr>
                <td><strong>TAR</strong></td>
                <td>Toolkit Application Reference</td>
            </tr>
            <tr>		    		    
                <td><strong>TCP</strong></td>
                <td>Transmission Control Protocol</td>
            </tr>
            <tr>
                <td><strong>TD-SCMACP</strong></td>
                <td>Time Division Synchronous Code Division Multiple Access</td>
            </tr>
            <tr>
                <td><strong>TDD</strong></td>
                <td>Time Domain Duplex</td>
            </tr>
            <tr>
                <td><strong>TLS</strong></td>
                <td>Transmission Layer Security</td>
            </tr>
            <tr>
                <td><strong>TVL</strong></td>
                <td>Type-Length-Value</td>
            </tr>
            <tr>
                <td><strong>TX</strong></td>
                <td>Transmit</td>
            </tr>
            <tr>
                <td><strong>TZ</strong></td>
                <td>Timezone</td>
            </tr>
            <tr>    
                <td><strong>TLS</strong></td>
                <td>Transport Layer Security</td>
            </tr>
	     <tr>
                <td><strong>UDH</strong></td>
                <td>User-Data-Header</td>
            </tr>
	     <tr>
                <td><strong>UDHL</strong></td>
                <td>UDH Length</td>
            </tr>
	     <tr>		     
                <td><strong>UDP</strong></td>
                <td>User Datagram Protocol</td>
            </tr>
           <tr>
                <td><strong>UICC</strong></td>
                <td>Universal Integrated Circuit Card</td>
            </tr>
           <tr>
                <td><strong>UML</strong></td>
                <td>Unified Modeling Language</td>
            </tr>
           <tr>
                <td><strong>UMTS</strong></td>
                <td>Universal Mobile Telephone System</td>
            </tr>
           <tr>
                <td><strong>URI</strong></td>
                <td>Uniform Resource Identifier</td>
            </tr>
           <tr>
                <td><strong>URN</strong></td>
                <td>Uniform Resource Name</td>
            </tr>
           <tr>
                <td><strong>USB</strong></td>
                <td>Unicode Transformation Format</td>
            </tr>
           <tr>
               <td><strong>UTC</strong></td>
                <td>Universal Time Coordinated</td>
            </tr>
           <tr>	      
                <td><strong>UTF</strong></td>
                <td>User Datagram Protocol</td>
            </tr>
           <tr> 
                <td><strong>UTRAN</strong></td>
                <td>UMTS Terrestrial Radio Access Network</td>
            </tr>
           <tr>
                <td><strong>UICC</strong></td>
                <td>Universally Unique Identifier</td>
            </tr>
           <tr>
                <td><strong>WAP</strong></td>
                <td>Wireless Application Protocol</td>
            </tr>
           <tr>
                <td><strong>WCDMA</strong></td>
                <td>Wideband Code Division Multiple Access</td>
            </tr>
           <tr>
                <td><strong>WDP</strong></td>
                <td>Wireless Datagram Protocol</td>
            </tr>
           <tr>
                <td><strong>WiMAX</strong></td>
                <td>Worldwide Interoperability for Microwave Access</td>
            </tr>
           <tr>
                <td><strong>WLAN</strong></td>
                <td>Wireless Local Area Network</td>
            </tr>
           <tr>
                <td><strong>WSP</strong></td>
                <td>Wireless Session Protocol</td>
            </tr>
           <tr>
                <td><strong>XML</strong></td>
                <td>eXtensible Markup Language</td>
            </tr>
           <tr>
        </tbody>            
</table>

## Introduction

This enabler defines the application layer communication protocol between an LwM2M Server and an LwM2M Client as well as between the LwM2M Bootstrap-Server and the LwM2M Client. The LwM2M Device includes an LwM2M Client component. The OMA Lightweight M2M enabler includes device management and service enablement for LwM2M Devices. The target LwM2M Devices for this enabler are mainly resource constrained devices. Therefore, this enabler makes use of lightweight and compact protocol mechanisms, as well as an efficient resource data model.

The LwM2M messaging layer is inspired by the RESTful design model based on \[CoAP\]. Interactions are between clients and servers using request/response model. Uniform Resource Identifiers (URIs) are used to identify and interact with object and resources while the protocol allows stateless and layered architecture.

Four interfaces are designed between the three entities, as shown in the architecture in [Figure The overall architecture of the LwM2M Enabler]():

-   Bootstrap

-   Client Registration

-   Device Management and Service Enablement

-   Information Reporting

<figure class="text-center">
      <img src="images/overall_architecture.svg" alt="LwM2M Architecture ">
      <figcaption>The overall architecture of the LwM2M Enabler</figcaption>
</figure>

### Version 1.2

Version 1.2 of LwM2M introduced the following objects, which are part of core specification:

* LwM2M COSE (Object ID:23)

* MQTT Server (Object ID:24)

* LwM2M Gateway (Object ID:25)

* LwM2M Gateway Routing (Object ID:26)

* 5G-NR Connectivity Object (Object ID:27)

Version 1.2 of LwM2M modified the following objects, which are part of core specification:

* Security Object (Object ID:0)

* Server Object  (Object ID:1)

* Firmware Update Object (Object ID:5)

* OSCORE Object (Object ID:21)

### Version 1.1

\[LwM2m-TS\_1.1\] introduced the following objects, which are part of core specification:

* OSCORE Object (Object ID:21)

\[LwM2m-TS\_1.1\] modified the following objects, which are part of core specification:

* Security Object (Object ID:0)

* Server Object (Object ID:1)

* Device Object (Object ID:3)

* Connectivity Monitoring Object (Object ID:4)

### Version 1.0

\[LwM2M-TS\_1.0\] introduced the following objects, which are part of core specification:

* Security Object (Object ID:0)

* Server Object (Object ID:1)

* Access Control Object (Object ID:2)

* Device Object (Object ID:3)

* Connectivity Monitoring Object (Object ID:4)

* Firmware Update Object (Object ID:5)

* Location Object (Object ID:6)

* Connectivity Statistics Object (Object ID:7)

## Fundamental Considerations

### Attributes

#### Attributes Definitions and Rules

Attributes are metadata which can be attached to an Object, an Object Instance, or a Resource. The value of an Attribute is LwM2M Server specific. These attributes can fulfil various roles, from carrying information only (e.g. Discover) to carrying parameters for setting up certain actions on the LwM2M Client (e.g. Notifications).

Attributes attached to Objects, Object Instances, Resources are respectively named O-Attribute, OI-Attribute, R-Attribute.

These Attributes MAY be carried in the message payload of Registration and Discover operations; they also MAY be updated - when writable - through the "Write-Attributes" operation.

Regardless to the LwM2M entity a given Attribute is attached to, the value of such an Attribute can be assigned at various levels: Object, Object Instance, Resource levels. Additionally, precedence rules apply when the same Attribute receives a value at different levels.

The rules below govern the usage of LwM2M Attributes,

*   The value of an O-Attribute MAY only be set at the Object level.

*   The value of an OI-Attribute MAY be set at the Object Instance level, and at the Object level.

    precedence rules:

    * Rule 1: When set at both levels, the value of the OI-Attribute set at Object Instance level will prevail.
    * Rule 2: When the Attribute value is set at the Object level, the scope of the OI-Attribute value extends to all the Instances of that Object, as long as the Rule 1 is respected.

*   An R-Attribute MAY be set at 4 different levels: the Resource Instance level, the Resource level, the Object Instance level and the Object level. Typically, an R-Attribute attached to a Multiple-Instance resource, can be set with an individual value to any Instance of such a Multiple-Instance Resource.

    precedence rules:

    * Rule 3: When set at the Resource level, the value of an R-Attribute prevails for that Resource whatever a value for this R-Attribute is also specified at an upper level (Object or Object Instance level).
      * Rule 3a: in the particular case this Resource is a Multiple-Instance Resource, the value of the R-Attribute set at the Resource Instance level will prevail over the value of the same Attribute set at the Resource level.
    * Rule 4: When set at the Object Instance level, the scope of an R-Attribute value extends to all the Resources of that Object Instance as long as the Rule 3 is respected.
    * Rule 5: When set at the Object level, the scope of an R-Attribute value extends to all the resources of any Instance of that Object, as long as the Rule 4 is respected.
    

{:page-break}

An attribute is fully determined by several characteristics, which are listed in [Table Attribute Characteristics]().

<table>
    <caption>Attribute Characteristics</caption>
    <thead>
        <tr>
            <th>Attribute characteristic</th>
            <th>Description</th> 
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> Name </td>
            <td> Attribute Name used to reference a specific Attribute in that Enabler (e.g. "Minimum Period") </td>
        </tr>
        <tr>
            <td> CoRE Link Param </td>
            <td> The encoding used when this Attribute is transferred through a CoRE link parameter. See section 2 of [RFC6690] </td>
        </tr>
        <tr>
            <td> Attachment </td>
            <td> The Object, Object Instance, or Resource, to which an Attribute is logically applied </td>
        </tr>
        <tr>
            <td> Assignation Level </td>
            <td> The Level (Object, Object Instance, Resource, Resource Instance) where the value of the Attribute is set (by WRITE-ATTRIBUTES). </td>
        </tr>
        <tr>
            <td> Class </td>
            <td> 
                Attributes are organized according to their purpose;<br/>
                2 Class of Attributes are supported<br/>
                &lt;NOTIFICATION&gt; gather Attributes regarding Notify operations parameters<br/>
                &lt;PROPERTIES&gt; gather Attributes regarding general information<br/>
            </td>
        </tr>
        <tr>
            <td> Access Mode </td>
            <td> R, W, RW: operation allowed by the LwM2M Server. </td>
        </tr>
        <tr>
            <td> Applicability </td>
            <td> Condition to fulfil for allowing to attach such an Attribute </td>
        </tr>
        <tr>
            <td> Default Value </td>
            <td> &lt;value&gt; or "-" or " "  </td>
        </tr>
        <tr>
            <td> Value Type </td>
            <td> Data Type (Refer <a href="">Data Types (Normative)</a>)  </td>
        </tr>
        <tr>
            <td> Value </td>
            <td> The Value carried by this Attribute : its data type must be of "Value Type" </td>
        </tr>
    </tbody> 
</table>

Some Attributes MAY be exposed to the LwM2M Server in the payload response to a "Discover" operation (Section [Discover Operation]()).

The value of some Attributes MAY be changed by the LwM2M Server in using the "Write-Attributes" operation (Section [Write-Attributes Operation]() ); which Attribute are concerned are marked as "W" (writable) in the table of the next section.

Note: A payload response to a "Discover" operation is a list of application/link-format CoRE Links \[RFC6690\], which will include the LwM2M Attributes.

#### Attributes Classification

&lt;PROPERTIES&gt; Class Attributes

The role of these Attributes is to provide metadata which may communicate helpful information to the LwM2M Server for example easing data management.

The LwM2M Server and LwM2M Client SHOULD support [Table &lt;PROPERTIES&gt; Class Attributes](), except when specifically mentioned as not required.

{:page-break}

<table>
    <caption>&lt;PROPERTIES&gt; Class Attributes</caption>
    <thead>
        <tr>
            <th>Attribute Name</th>
            <th>CoRE Link param</th>
            <th>Attachment</th>
            <th>Assignation Level</th>
            <th>Support Required</th>
            <th>Access Mode</th>
            <th>Value Type</th>
            <th>Default Value</th>
            <th>Applicability</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Dimension</td>
            <td>"dim" "=" 1*DIGIT</td>
            <td>Resource</td>
            <td>Resource</td>
            <td>YES (Client)</td>
            <td>R</td>
            <td>Integer [0:255]</td>
            <td>-</td>
            <td>Multiple-Instance Resource</td>
            <td>Number of instances existing for a Multiple-Instance Resource</td>
        </tr>
        <tr>
            <td>Short Server ID</td>
            <td>"ssid" "=" 1*DIGIT</td>
            <td>Object Instance</td>
            <td>Object Instance</td>
            <td>YES (Client)</td>
            <td>R</td>
            <td>Integer [1:65534]</td>
            <td>-</td>
            <td>Security, Server and OSCORE Objects</td>
            <td>Provides the LwM2M Server Short ID information (see Section <a href="">Bootstrap-Discover Operation</a>)</td>
        </tr>
        <tr>
            <td>Server URI</td>
            <td>"uri" "=" quoted-string</td>
            <td>Object Instance</td>
            <td>Object Instance</td>
            <td>YES (Client)</td>
            <td>R</td>
            <td>String</td>
            <td>-</td>
            <td>Security Object</td>
            <td>Provides the LwM2M Server URI information (see Section <a href="">Bootstrap-Discover Operation</a>)</td>
        </tr>
        <tr>
            <td>Object Version</td>
            <td>"ver" "=" 1*DIGIT "." 1*DIGIT</td>
            <td>Object</td>
            <td>Object</td>
            <td>YES (Server) YES (Client) when able to support Objects in version &gt; 1.0</td>
            <td>R</td>
            <td>String</td>
            <td>1.0</td>
            <td></td>
            <td>Provides the version of the associated Object. The rules governing the usage of this parameter are specified in <a href="">Object Definition and Object Version Usage</a>.</td>
        </tr>
        <tr>
            <td>Enabler Version</td>
            <td>"lwm2m" "=" 1*DIGIT "." 1*DIGIT</td>
            <td>None</td>
            <td>None</td>
            <td>YES (Server) YES (Client)</td>
            <td>R</td>
            <td>String</td>
            <td>-</td>
            <td></td>
            <td>Provides the version of the supported LwM2M Enabler.</td>
        </tr>
    </tbody>
</table>

&lt;NOTIFICATION&gt; Class Attributes

The role of these R-Attributes is to provide parameters to the "Notify" operation; any readable Resource can have such R-attributes.

Note: For readability in the remaining part of this section, the term "Resource" will be used to designate either a Single-Instance Resource or an Instance of a Multiple-Instance Resource, according to the nature of the considered Resource (i.e. Single- or Multiple-Instance Resource).

In the message sent by an LwM2M Client in response to an "Observe" operation, the current Resource value is reported; this event can be considered as the initial notification.

Each time a Resource notification is sent, the "Minimum Period" and "Maximum Period" timers associated to this Resource are restarted.

Notification Conditions: the notification of a Resource value will be sent when:
- a valid Change Value Condition ("Greater Than", "Less Than", OR "Step") - if any is defined - 
  AND the "Minimum Period" Timing Conditions are both fulfilled for that Resource OR
- the "Maximum Period" Timing Condition is fulfilled.

Additionally, the following rules MUST be considered:
- a "Maximum Period" (pmax) applied to a Resource that is smaller than the "Minimum Period" applied to the same Resource MUST be ignored for that Resource,
- the "Change Value Conditions" are considered as valid, if the two following rules related to the Attributes defined in the table below ("Greater Than", "Less Than", "Step") are respected:
     *   **("lt" value &lt; "gt" value)**
     *   **("lt" value + 2\*"st" values &lt;"gt" value)**

When the "Change Value Conditions" Attributes are set in a single Write-Attributes operation, the operation MUST be rejected when the rules above are violated. 

The "Minimum Evaluation Period" (epmin) and "Maximum Evaluation Period" (epmax) values can be used to configure the device to perform reporting evaluations. After the expiry of epmin, the device MAY immediately perform an evaluation per the "Notification Conditions" above. After the expiry of epmax, the device MUST perform an evaluation per the "Notification Conditions". If both the epmin and epmax attributes are defined, the epmin value must be less than the epmax value.

The behaviour of Notification class attributes MUST follow \[DynLink\] unless stated otherwise in this specification.
Note: The attributes epmin, epmax, con, hqmax and edge are specified in this specification but currently not referenced in \[DynLink\]. \[DynLink\], however, introduced the Notification Band (band) attribute, which is not used in this version of LwM2M specification.

The LwM2M Server MUST support and LwM2M Client SHOULD support all the &lt;NOTIFICATION&gt; Class Attributes listed in [Table &lt;NOTIFICATION&gt; class Attributes]().

<table>
    <caption>&lt;NOTIFICATION&gt; class Attributes</caption>
    <thead>
    <tr>
        <th>Attribute Name</th>
        <th>CoRE Link param</th>
        <th>Attachment</th>
        <th>Assignation Level</th>
        <th>Required</th>
        <th>Access Mode</th>
        <th>Value Type</th>
        <th>Default Value</th>
        <th>Apply Condition</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Minimum Period</td>
        <td>"pmin" "=" 1*DIGIT</td>
        <td>Resource</td>
        <td>Resource<br>Resource&nbsp;Instance<br>Object<br>Object&nbsp;Instance</td>
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>0 (sec)</td>
        <td>Readable Resource</td> 
    </tr> 
    <tr>
        <td colspan="9"><em>Notes:</em> The Minimum Period Attribute indicates the minimum time in seconds the LwM2M Client MUST wait between two notifications. If a notification of an observed Resource is supposed to be generated but it is before pmin expiry, notification MUST be sent as soon as pmin expires. In the absence of this parameter, the Minimum Period is defined by the Default Minimum Period set in the LwM2M Server Account.</td>
    </tr>
    <tr> 
        <td>Maximum Period</td> 
        <td>"pmax" "=" 1*DIGIT</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance<br>Object<br>Object Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>-</td>
        <td>Readable Resource</td> 
    </tr>
    <tr>
        <td colspan="9"><em>Notes:</em> The Maximum Period Attribute indicates the maximum time in seconds the LwM2M Client MAY wait between two notifications. When this "Maximum Period" expires after the last notification, a new notification MUST be sent. In the absence of this parameter, the "Maximum Period" is defined by the Default Maximum Period when set in the LwM2M Server Account or considered as 0 otherwise. The value of 0, means pmax MUST be ignored. The maximum period parameter MUST be greater than or equal to the minimum period parameter otherwise pmax will be ignored for the Resource to which such inconsistent timing conditions are applied.</td>
    </tr>
    <tr> 
        <td>Greater Than</td> 
        <td>"gt" "=" 1*DIGIT ["." 1*DIGIT]</td>
        <td>Resource</td> 
        <td>Resource<br>Resource Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Float</td> 
        <td>-</td> 
        <td>Numerical &amp; Readable Resource</td> 
    </tr>
    <tr> <td colspan="9"><em>Notes:</em> This "gt" Attribute defines a threshold high value. When this Attribute is present, the LwM2M Client MUST notify the Server each time the Observed Resource value crosses this threshold with respect to the pmin parameter and valid "Change Value Conditions" (see Notification Conditions above).</td>
    </tr>
    <tr>  
        <td>Less Than</td> 
        <td>"lt" "=" 1*DIGIT ["." 1*DIGIT]</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Float</td> 
        <td>-</td>
        <td>Numerical &amp; Readable Resource</td> 
    </tr>
    <tr>  
        <td colspan="9"><em>Notes:</em> This "lt" Attribute defines a threshold low value. When this Attribute is present, the LwM2M Client MUST notify the Server each time the Observed Resource value crosses this threshold with respect to the pmin parameter and valid "Change Value Conditions" (see Notification Conditions above).</td>
    </tr>
    <tr>
        <td>Step</td> 
        <td>"st" "=" 1*DIGIT ["." 1*DIGIT]</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Float</td> 
        <td>-</td> 
        <td>Numerical &amp; Readable Resource</td>
    </tr>
    <tr>
        <td colspan="9"><em>Notes:</em> This "Step" Attribute defines a minimum change value between two notifications. When this Attribute is present, the Change Value Condition will occur when the value variation since the last notification of the Observed Resource, is greater or equal to the "Step" Attribute value. When the "Step" Change Value Condition occurs, the LwM2M Client MUST notify the Server with respect to pmin parameter and "Valid Value Conditions" (see notification Conditions above).</td>
    </tr>
    <tr>
        <td>Minimum Evaluation Period</td>
        <td>"epmin" "=" 1*DIGIT</td>
        <td>Resource</td>
        <td>Resource<br>Resource Instance<br>Object<br>Object Instance</td>
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>-</td>
        <td>Readable Resource</td> 
    </tr> 
    <tr>
        <td colspan="9"><em>Notes:</em> The Minimum Evaluation Period Attribute indicates the minimum time in seconds the LwM2M Client MUST wait between two evaluations of reporting criteria. In the absence of this parameter, the Evaluation Minimum Period is not defined.</td>
    </tr>
    <tr> 
        <td>Maximum Evaluation Period</td> 
        <td>"epmax" "=" 1*DIGIT</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance<br>Object<br>Object Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>-</td>
        <td>Readable Resource</td> 
    </tr>
    <tr>
        <td colspan="9"><em>Notes:</em> The Maximum Evaluation Period Attribute indicates the maximum time in seconds the LwM2M Client MAY wait between two evaluations of reporting criteria. When the Maximum Evaluation Period expires after the previous evaluation, a new evaluation MUST occur. In the absence of this parameter, the Maximum Evaluation Period is not defined.</td>
    </tr>
<tr> 
        <td>Edge</td> 
        <td>"edge" "=" ( "0" / "1" )</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>-</td>
        <td>Boolean &amp; Readable Resource</td> 
    </tr>
    <tr>
        <td colspan="9"><em>Notes:</em> The Edge Attribute indicates either the falling edge ("0") or the rising edge ("1") transition of a Boolean Resource. When this Attribute is present, the LwM2M Client MUST notify the Server each time the Observed Resource value goes from "true" to "false" (edge = "0"), or from "false" to "true" (edge = "1") with respect to the pmin parameter and valid "Change Value Conditions" (see Notification Conditions above).</td>
    </tr>
	  <tr> 
        <td>Confirmable Notification</td> 
        <td>"con" "=" ( "0" / "1" )</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance<br>Object<br>Object Instance</td> 
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>-</td>
        <td>Readable Resource</td> 
    </tr>
    <tr>
        <td colspan="9"><em>Notes:</em> The Notification Confirmable Attribute indicates whether a Notification resulting from an Observation of a specific Object, Object Instance, Resource, Resource Instance MUST be sent over confirmable transport. If a Notification includes several Objects or Object Instances or Resources or Resource Instances or a combination thereof, then this Notification MUST be sent over confirmable transport if at least one of the Notification components has con=1.</td>
    </tr>  
<tr> 
        <td>Maximum Historical Queue</td> 
        <td>"hqmax" "=" 1*DIGIT</td> 
        <td>Resource</td> 
        <td>Resource<br>Resource Instance<br>Object<br>Object Instance</td>
        <td>No</td> 
        <td>RW</td> 
        <td>Integer</td> 
        <td>-</td>
        <td>Readable Resource</td> 
    </tr>
    <tr>	
      <td colspan="9"><em>Notes:</em> The Maximum Historical Queue Attribute indicates how many entries of historical data resulting from an Observation of a specific Object, Object Instance, Resource, Resource Instance MUST be stored, e.g. while the LwM2M Client is offline, or, the LwM2M Server account is disabled. If this attribute is present, only the data of Objects, Object Instances, Resources, Resource Instances with hqmax>0 will be included in notifications which were stored while disabled or offline. Historical notifications MAY be sent in a format as described in Section [SenML JSON](). If the queue size reaches hqmax and a new reading is received, the oldest reading MUST be dropped. The LwM2M Client SHOULD empty the queue as soon it becomes aware that connectivity has been restored. The use of "hqmax" is dependent on notification storing being enabled via the "Notification Storing When Disabled or Offline" Resource of the LwM2M Server Object.</td>
    </tr>
    </tbody>
</table>


Examples illustrating Attributes setting are provided in Section [Figure Example flows of Device Management & Service Enablement Interface]().

### Compatibility

#### LwM2M Server and LwM2M Client Versions

The LwM2M Server MUST support an LwM2M Client of the same major and minor version. In the case of the current version, an LwM2M Server whose version is 1.2 MUST support an LwM2M Client whose version is 1.2.

The LwM2M Server SHOULD support all LwM2M Client versions of the same major version. Backward compatibility with a common major version is strongly recommended to support deployment scenarios where LwM2M Servers are updated before the LwM2M Clients. For example, an LwM2M Server whose version is 1.2 should support LwM2M Clients that are version 1.0 or 1.1. Forward compatibility with a common major version is also recommended to support deployment scenarios where the LwM2M Clients are updated before the LwM2M Server. For example, an LwM2M Server whose version is 1.1 should support an LwM2M Client whose version is 1.2.

The LwM2M Server MAY support LwM2M Clients of an earlier major version. As an example, an LwM2M Server whose version is 2.0 MAY support an LwM2M Client whose version is 1.1. This type of backward compatibility is recommended, when it is possible, to support deployment scenarios where LwM2M Servers are updated before the LwM2M Clients.

#### Optional Objects and Object Versions

Operations initiated by the LwM2M Client to the LwM2M Server may address optional objects that are not supported by the LwM2M Server. Similarly, operations initiated by the LwM2M Server to the LwM2M Client may address objects that are not supported by the LwM2M Client. This may occur because the objects are not recognized or the object versions are not compatible.

#### Optional Resources

Operations initiated by the LwM2M Client to the LwM2M Server may address optional resources that are not supported by the LwM2M Server. Operations initiated by the LwM2M Server to the LwM2M Client may address optional resources that are not supported by the LwM2M Client.

To enable compatibility between LwM2M Clients and LwM2M Servers for optional resources that are not supported, the LwM2M Client or LwM2M Server, when possible, MUST NOT interpret transactions targeted at those resources as errors.

## Interfaces

According to [Figure The overall architecture of the LwM2M Enabler]() there are four interfaces: 1) Bootstrap, 2) Client Registration, 3) Device Management and Service Enablement, and 4) Information Reporting. The operations for the four interfaces can be classified into uplink operations and downlink operations. The operations for each interface are defined in this section, and then mapped to protocol mechanisms in the LwM2M Transport specification \[LwM2M-TRANSPORT\].

[Figure Bootstrap Interface with Bootstrap-Request operation]() and [Figure Bootstrap Interface with Bootstrap-Pack-Request operation]() shows the operation model for the "Bootstrap" interface. For this interface, the operations are uplink operations named "Bootstrap-Request" and "Bootstrap-Pack-Request", downlink operations named "Bootstrap-Discover", "Bootstrap-Write", "Bootstrap-Read","Bootstrap-Delete" and "Bootstrap-Finish". These operations are used to initialize the needed Object(s) for the LwM2M Client to register with one or more LwM2M Server(s). When a "Bootstrap-Write" operation initiated on the "Bootstrap" interface by the LwM2M Bootstrap-Server, the LwM2M Client MUST write the value included in the payload regardless of an existence of the targeting Object Instance(s) or Resource(s) and access rights. In the mode where the LwM2M Bootstrap-Server is addressing the Bootstrap Information to the LwM2M Client when initiated with "Bootstrap-Request", the LwM2M Bootstrap-Server MUST inform the LwM2M Client when this transfer is over by sending a "Bootstrap-Finish" operation.

In addition to the bootstrapping interface the required information for the LwM2M Client to function with LwM2M Server(s) may also be configured during manufacturing (called Factory Bootstrap) or via a smartcard (called Smartcard Bootstrap).

<figure class="text-center">
      <img src="images/bootstrap.svg" alt="Bootstrap-Request">
      <figcaption>Bootstrap Interface with Bootstrap-Request operation</figcaption>
</figure>

<figure class="text-center">
      <img src="images/bootstrap-pack.svg" alt="Bootstrap-Pack-Request">
      <figcaption>Bootstrap Interface with Bootstrap-Pack-Request operation</figcaption>
</figure>

[Figure Client Registration]() shows the operation model for the interface "Client Registration". For this interface, the operations are uplink operations named "Registration", "Update" and "De-register".

<figure class="text-center">
      <img src="images/client_registration.svg" alt="Client Registration">
      <figcaption>Client Registration</figcaption>
</figure>

[Figure Device Management and Service Enablement]() shows the operational model for the "Device Management and Service Enablement" interface. For this interface, the downlink operations are "Read", "Read-Composite", "Create", "Delete", "Write", "Write-Composite", "Execute", "Write-Attributes", and "Discover". These operations are used to interact with Resources, Resource Instances, Objects, Object Instances and/or their attributes exposed by the LwM2M Client. The "Read" and "Read-Composite" operations are used to read the current values. The "Discover" operation is used to discover attributes and to discover which Resources are implemented in a certain Object. The "Write" and "Write-Composite" operations are used to update values. The "Write-Attributes" operation is used to change attribute values. The "Execute" operation is used to initiate an action. The "Create" and "Delete" operations are used to create and delete Instances, respectively.

<figure class="text-center">
      <img src="images/device_management_service_enablement.svg" alt="Device Management and Service Enablement">
      <figcaption>Device Management and Service Enablement</figcaption>
</figure>


[Figure Information Reporting]() shows the operational model for the "Information Reporting" interface. For this interface, the downlink operations are "Observe", "Observe-Composite", "Cancel Observation", and "Cancel Observation-Composite". The "Notify" is an uplink operation, which is used to send a new value of a Resource from the LwM2M Client to the LwM2M Server. The "Send" operation is another uplink operation which is used by the LwM2M Client to send data to the LwM2M Server.

<figure class="text-center">
      <img src="images/information_reporting.svg" alt="Information Reporting">
      <figcaption>Information Reporting</figcaption>
</figure>

The relationship between operations and interfaces is listed in [Table Relationship of operations and interfaces]().

<table>
    <caption>Relationship of operations and interfaces</caption>
    <thead>
        <tr>
            <th>Interface</th>
            <th>Direction</th>
            <th>Operation</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Bootstrap</td>
            <td>Uplink</td>
            <td>Bootstrap-Request, Bootstrap-Pack-Request</td>
        </tr>
        <tr>
            <td>Bootstrap</td>
            <td>Downlink</td>
            <td>Bootstrap-Write, Bootstrap-Read, Bootstrap-Discover, Bootstrap-Delete, Bootstrap-Finish</td>
        </tr>
        <tr>
            <td>Client Registration</td>
            <td>Uplink</td>
            <td>Register, Update, De-register</td>
        </tr>
        <tr>
            <td>Device Management and Service Enablement</td>
            <td>Downlink</td>
            <td>Create, Read, Read-Composite, Write, Delete, Execute, Write-Attributes, Write-Composite, Discover</td>
        </tr>          
        <tr>
            <td>Information Reporting</td>
            <td>Downlink</td>
            <td>Observe, Observe-Composite, Cancel Observation, Cancel Observation-Composite</td>
        </tr>
        <tr>
            <td>Information Reporting</td>
            <td>Uplink</td>
            <td>Notify, Send</td>
        </tr>
    </tbody>
</table>

### Bootstrap Interface

The Bootstrap Interface is used to provision essential information into the LwM2M Client to enable the LwM2M Client to perform the "Register" operation with one or more LwM2M Servers.

There are four bootstrap modes supported by the LwM2M Enabler:

-   Factory Bootstrap

-   Bootstrap from Smartcard

-   Client Initiated Bootstrap

-   Server Initiated Bootstrap

The last two Bootstrap modes require the help of an LwM2M Bootstrap-Server to achieve the ultimate goal to connect an LwM2M Client to their LwM2M Server(s). As specified in Section [Server Initiated Bootstrap](), the "Server Initiated Bootstrap" mode is a method to invoke the "Client Initiated Bootstrap" mode.

The LwM2M Client MUST support at least one bootstrap mode specified in the Bootstrap Interface.

The LwM2M Bootstrap-Server MUST support the "Client Initiated Bootstrap" mode with the "Bootstrap-Request" operation specified in the Bootstrap Interface. The LwM2M Bootstrap-Server MAY support the "Client Initiated Bootstrap" mode with the "Bootstrap-Pack-Request" operation specified in the Bootstrap Interface.

This section describes what information is conveyed across the Bootstrap Interface, where the LwM2M Client puts that information and how to provision the Bootstrap Information for each of these bootstrap modes. \[LwM2M-TRANSPORT\] provides further security-relevant information concerning the bootstrap techniques. <span id="_Ref339619648" class="anchor"></span>

#### LwM2M Bootstrap-Server 

The LwM2M Bootstrap-Server is used to provision the LwM2M Client with the information required to contact the LwM2M Server(s).

In order for the LwM2M Client and the LwM2M Bootstrap-Server to establish a connection on the Bootstrap Interface, either in Client Initiated Bootstrap mode or in Server Initiated Bootstrap mode, the LwM2M Client MUST have an LwM2M Bootstrap-Server Account pre-provisioned.

Note: During the Bootstrap Phase the LwM2M Client MAY ignore requests and flush all pending responses not related to the Bootstrap sequence. 

#### Bootstrap Information

This section specifies the information that needs to be configured for an LwM2M Client to connect to LwM2M Server(s) or to the LwM2M Bootstrap-Server. This Bootstrap Information can be available before performing the Bootstrap Sequence described in Section [Bootstrap Sequence]() or obtained as a result of the Bootstrap Sequence.

Bootstrap Information can be categorized into two types:

-   LwM2M Server Bootstrap Information

-   LwM2M Bootstrap-Server Bootstrap Information

<table>
    <caption>Bootstrap Information List</caption>
    <thead>
        <tr>
            <th>Bootstrap Information Type</th>
            <th>Entity</th>
            <th>Required</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2">The LwM2M Server Bootstrap Information</td>
            <td>LwM2M Server Account</td>
            <td>Yes*</td>
        </tr>
        <tr>
            <td>Additional Object Instances (e.g. Access Control, Connectivity Monitoring Object)</td>
            <td>No</td> 
        </tr>
        <tr>
            <td>The LwM2M Bootstrap-Server Bootstrap Information</td>
            <td>LwM2M Bootstrap-Server Account<br>
                (Security Object Instance + potential OSCORE Object Instance)</td>
            <td>No</td> 
        </tr>
    </tbody>
</table>

The LwM2M Client MUST have the LwM2M Server Bootstrap Information after the bootstrap sequence specified in Section [Bootstrap Sequence](). The LwM2M Server Bootstrap Information is used by the LwM2M Client to register and connect to the LwM2M Server.

The LwM2M Client SHOULD have the LwM2M Bootstrap-Server Bootstrap Information. The LwM2M Server Bootstrap Information MUST contain at least one LwM2M Server Account.

Note that according to the LwM2M Server Account definition, a usual LwM2M Server Account is composed of a Security Object Instance and a Server Object Instance which are paired by sharing (respectively in Resource 10 and Resource 0 of that Objects) the same Short Server ID; a Short Server ID being unique in the LwM2M Client. Note also that a Security Object Instance may potentially be associated to an OSCORE Object Instance by means of an Object Link (Resource 17 of the Security Object Instance).

The LwM2M Server Bootstrap Information MAY additionally contain further Object Instances (e.g. Access Control, Connectivity Monitoring Object).

The LwM2M Client MAY be configured to use one or more LwM2M Server Account(s).

The LwM2M Client MUST have at most one LwM2M Bootstrap-Server Account.

The LwM2M Bootstrap-Server Bootstrap Information is used by the LwM2M Client to contact the LwM2M Bootstrap-Server to get the LwM2M Server Bootstrap Information.

The LwM2M Bootstrap-Server Bootstrap Information MUST be an LwM2M Bootstrap-Server Account.

(*) The LwM2M Client MUST have at least one LwM2M Server Account after completion of Bootstrap Sequence specified in Section [Bootstrap Sequence]().

Please note that the LwM2M Client MUST accept Bootstrap Information sent via Bootstrap Interface without applying access control, as specified in Section [Authorization]().

#### Bootstrap Modes

The following sub-sections provide further information for the four Bootstrap modes.

##### Factory Bootstrap

In this mode, the LwM2M Client has been configured with the necessary bootstrap information prior to deployment of the device. The configured information may be the LwM2M Bootstrap-Server Bootstrap Information and/or the LwM2M Server Bootstrap Information. 

##### Bootstrap from Smartcard

When the Device supports a Smartcard, the LwM2M Client MUST retrieve and process the bootstrap data contained in the Smartcard as described in [Storage of LwM2M Bootstrap Information on the Smartcard (Normative)](). When the bootstrap data retrieval is successful, the LwM2M Client MUST process the bootstrap data from the Smartcard and SHOULD apply the Bootstrap Information to its configuration to enhance security benefits.

Due to the sensitive nature of the Bootstrap Information, a secure channel SHOULD be established between the Smartcard and the LwM2M Device.

When such a secure channel is established between the Smartcard and the LwM2M Device, this secure channel MUST be based on \[GLOBALPLATFORM\] procedure, mainly described in Section [Secure channel between Smartcard and LwM2M Device
Storage for secure Bootstrap Data provisioning (Normative)]().

In this Bootstrap mode, the LwM2M Client MUST also ensure that the bootstrap data previously retrieved from the Smartcard is unchanged within the Smartcard. If bootstrap data is changed, and if the previous Bootstrap Information was applied from Smartcard, this previous Bootstrap Information MUST be disabled in the LwM2M Client and the LwM2M Client SHOULD apply the new Bootstrap Information from Smartcard to its configuration.

If the Smartcard is disabled (e.g. removing the Smartcard) then the Bootstrap Information created from the bootstrap data of the previous Smartcard MUST be deleted.

Checking for Smartcard change and disabling MUST be performed by the LwM2M Client, each time a "Register" or "Update" operation take place, with an LwM2M Server provisioned from Smartcard. As usual, the Bootstrap security rules (see Section [Bootstrap Security]()) then apply.

NOTE: Bootstrap Information in Smartcard can be updated by using Smartcard OTA protocol as specified in \[ETSI 102 225\] / \[ETSI 102 226\] and extensions such as \[3GPP 31.115\] / \[3GPP 31.116\] and \[3GPP2 C.S0078-0\] / \[3GPP2 C.S0079-0\].

##### Client Initiated Bootstrap

The "Client Initiated Bootstrap" mode provides a mechanism for the LwM2M Client to retrieve Bootstrap Information from an LwM2M Bootstrap-Server. The "Client Initiated Bootstrap" mode requires an LwM2M Bootstrap-Server Account preloaded in the LwM2M Client.

At a minimum an LwM2M Client needs to have DTLS/TLS and/or OSCORE \[OSCORE\] security credentials preloaded to authenticate to an LwM2M Bootstrap-Server. 

Before entering the "Client Initiated Bootstrap" mode, the LwM2M Client may be registered to LwM2M Servers. Whether or not the LwM2M Client keeps these registrations active during the Client Initiated Bootstrap is implementation dependent.

[Figure Client Initiated Bootstrap with Bootstrap-Request operation]() and [Figure Client Initiated Bootstrap with Bootstrap-Pack-Request operation]() depict protocol exchange graphically for two different ways to perform Client Initiated Bootstrap. 

<figure class="text-center">
      <img src="images/procedure_client_initiated_bootstrap.svg" alt="Procedure of Client Initiated Bootstrap with Bootstrap-Request operation">
      <figcaption>Client Initiated Bootstrap with Bootstrap-Request operation</figcaption>
</figure>

<figure class="text-center">
      <img src="images/procedure_client_initiated_bootstrap_with_bootstrap_pack.svg" alt="Procedure of Client Initiated Bootstrap with Bootstrap-Pack-Request operation">
      <figcaption>Client Initiated Bootstrap with Bootstrap-Pack-Request operation</figcaption>
</figure>

Step \#0: Bootstrap-Request or Bootstrap-Pack-Request to bootstrap URI

The LwM2M Client sends a "Bootstrap-Request" or "Bootstrap-Pack-Request" operation to LwM2M Bootstrap-Server URI, which has been pre-provisioned. When requesting the bootstrap, the LwM2M Client SHOULD send the LwM2M Client's "Endpoint Client Name" as a parameter to allow the LwM2M Bootstrap-Server to provision the proper bootstrap information for the LwM2M Client. The LwM2M Client MAY omit "Endpoint Client Name" if it is equal to the identifier utilized in the security protocol.

Step \#1: Configure Bootstrap Information

The LwM2M Bootstrap-Server configures the LwM2M Client with the Bootstrap Information using the "Write" and/or "Delete" operations or using "Bootstrap-Pack", depending on the operation used in Step #0.

This Bootstrap mode MAY be used to configure some Resources of the Bootstrap Information in the LwM2M Client after initial bootstrap to update Bootstrap Information. In this case, all Bootstrap Information is OPTIONAL.

Step \#2: Bootstrap-Finish

When the LwM2M Server has finished sending the Bootstrap Information to the LwM2M Client, the Server MUST send the "Bootstrap-Finish" operation to the Client to properly end this phase. "Bootstrap-Finish" operation is not required if the Bootstrap Information is sent to the client using a "Bootstrap-Pack".

If "Bootstrap-Request" operation is used in Step #0, the bootstrap procedure fails when the LwM2M Client does not receive the "Bootstrap-Finish" operation after the EXCHANGE\_LIFETIME time period expired. The EXCHANGE\_LIFETIME parameter is defined in \[CoAP\].

Step \#3: Clean-up after successful Bootstrapping

Successful Bootstrapping means that the Bootstrap-Finish operation has been received by the LwM2M Client, if the "Bootstrap-Request" has been used in Step #0, and the loaded configuration is considered consistent by the LwM2M Client. In this case the Bootstrap-Finish response sent to the LwM2M Bootstrap-Server should indicate a success code. If Bootstrapping was unsuccessful, the Bootstrap-Server Account MUST retain the values it had before the unsuccessful Bootstrapping sequence started and further statements below in Step #3 do not apply. If Bootstrapping was unsuccessful using "Bootstrap-Pack-Request", the LwM2M Client MUST retry bootstrapping with "Bootstrap-Request".

In the case the LwM2M Client is registered to an LwM2M Server, if the matching LwM2M Server Account was deleted, the LwM2M Client MUST consider itself de-registered from the LwM2M Server. Note that if the matching LwM2M Server Account was modified, the LwM2M Client may need to update its registration to the LwM2M Server depending on the nature of the modifications.

If the Bootstrap-Server Account Timeout Resource is instantiated in the Security Object Instance of the Bootstrap-Server, the LwM2M Client MUST purge the LwM2M Bootstrap-Server Account after the expiration time provided by the value of this Resource. If this Resource is not instantiated or its value is set to 0, the Bootstrap-Server Account lifetime is infinite (Section [LwM2M Object: LwM2M Security]()).

High entropy keys that are unique per device SHOULD be used for the LwM2M Bootstrap-Server Account. In that case the LwM2M Bootstrap-Server Account SHOULD be kept after bootstrapping i.e. the Bootstrap-Server Account Timeout Resource may be set to 0, or may stay not instantiated.

In case the Bootstrap-Server Account has to be replaced, the replacement and the purge of the previous Bootstrap-Server Account MUST properly take place before the Client sends the Bootstrap-Finish response message back to the Bootstrap-Server; otherwise a "Not Acceptable" Response MUST be returned, and the previous Bootstrap-Server Account is still the only one active.

Note: If the original LwM2M Bootstrap-Server Account is purged from the device, and a new LwM2M Bootstrap-Server Account has not been created, further adding or removing of LwM2M Server Accounts will no longer be possible. Furthermore, updating security credentials e.g. X.509 certificates will also no longer be possible.

##### Server Initiated Bootstrap

In this mode the decision to trigger a Bootstrap Sequence is made by an authorized LwM2M Server. The LwM2M Server triggers the LwM2M Client to enter the "Client Initiated Bootstrap" mode rather than initiating a different protocol for configuring the Bootstrap Information in the LwM2M Client.

The trigger mechanism is performed through the execution of the "Bootstrap-Request Trigger" Resource available from the related Server Object Instance. A connection between an LwM2M Client and an LwM2M Server must already exist to enter this "Server Initiated Bootstrap" mode.

Note: proprietary mechanisms can be used to cause an LwM2M Client to enter the standard "Client Initiated Bootstrap" mode, but that is outside the scope of this specification. 

The figure below depicts the "Server Initiated Bootstrap" flow initiated by an authorized LwM2M Server.

<figure class="text-center">
      <img src="images/server_initiated_bootstrap_b.svg" alt="Procedure of Server Initiated Bootstrap initiated by an authorized LwM2M Server">
      <figcaption>Procedure of Server Initiated Bootstrap initiated by an authorized LwM2M Server</figcaption>
</figure>

#### Bootstrap Sequence

The LwM2M Client MUST respect step by step the procedural sequence specified below when attempting to bootstrap an LwM2M Device:

1.  If the LwM2M Device has Smartcard, the LwM2M Client tries to obtain Bootstrap Information from the Smartcard using the Bootstrap from Smartcard mode.
    Any Server Initiated Bootstrap attempt MUST be ignored by the LwM2M Client until it has tried to bootstrap via Smartcard or Factory Bootstrap mode.

2.  If the LwM2M Client is not configured using the Bootstrap from Smartcard mode, the LwM2M Client tries to obtain the Bootstrap Information by using Factory Bootstrap mode.
    Any Server Initiated Bootstrap attempt MUST be ignored by the LwM2M Client until it has tried to bootstrap via Smartcard or Factory Bootstrap mode.

3.  If the LwM2M Client has any LwM2M Server Object Instances from the previous steps, the LwM2M Client tries to register to the LwM2M Server(s) configured in the LwM2M Server Object Instance(s).

4.  If the LwM2M Client fails to register to all the LwM2M Servers or the Client doesn't have any LwM2M Server Object Instances, the LwM2M Client performs the Client Initiated Bootstrap.

5.  A Server Initiated Bootstrap attempt (e.g. for updating an LwM2M Server Account) remains possible, but only if the LwM2M Client retains the corresponding LwM2M Bootstrap-Server Account.

#### Bootstrap Security

The information conveyed through the Bootstrap Interface is sensitive and requires communication security to be used. The security requirements for the Bootstrap Interface is discussed in \[LwM2M-TRANSPORT\].

#### Bootstrap and Configuration Consistency

When a Bootstrap Information is loaded in the LwM2M Client, any detected inconsistency MUST be reported in sending an error response code to the Bootstrap-Finish operation. If the Bootstrap Information is delivered to the LwM2M Client with "Bootstrap-Pack", in case of any inconsistency, the LwM2M Client MUST retry bootstrapping with "Bootstrap-Request" operation.

As an example, during a Bootstrap phase, a Multi-Servers Configuration is loaded in an LwM2M Client with the associated Instances of the Access Control Object, while this particular LwM2M Client is not supporting the Access Control Object itself (Single Server context support only). In that case, the client is not able to find a satisfactory consistent configuration by itself, so that the Bootstrap sequence cannot be ended successfully.

On receipt of the error response code to the Bootstrap-Finish operation, the Bootstrap-Server MAY take corrective actions before issuing a new Bootstrap-Finish operation.

As specified in Section [Bootstrap Modes](), the LwM2M Client MUST consider the Bootstrap procedure is failed when the LwM2M Client didn't receive a Bootstrap-Finish operation in a certain period (EXCHANGE\_LIFETIME), if the bootstrap was initiated with "Bootstrap-Request" operation.

#### Bootstrap Operations

The mapping to underlying transports is detailed in \[LwM2M-TRANSPORT\].

The Bootstrap operations are used to help the Bootstrap-Server of setting a proper configuration in an LwM2M Client especially in the case of an incremental Bootstrap procedure for which a particular care  must be observed to preserve the Client consistency (e.g. adding  a new Server Account without breaking the access rights already in place in the targeted LwM2M Client). 


##### Bootstrap-Request Operation

The Bootstrap-Request operation is only performed to initiate the Bootstrap Sequence in the "Client Initiated Bootstrap" mode.

{:page-break}

The Bootstrap-Request operation has the following parameters:

<table>
    <caption>Bootstrap-Request Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Endpoint Client Name</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the LwM2M Client's "Endpoint Client Name". This parameter is optional if it is equal to the identifier in the security protocol and deployment is such that the security protocol identifier is always available for the server (e.g. no proxies in between).</td>
        </tr>
        <tr>
            <td>Preferred Content Format</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the numeric ID of the LwM2M Client's preferred Content Format for bootstrap configuration. The Content Format ID MUST be one of the SenML JSON, SenML CBOR, LwM2M CBOR, or TLV formats defined in Section <a href="">Data Formats for Transferring Resource Information</a>. </td>
        </tr>
    </tbody>
</table>

##### Bootstrap-Finish Operation

The Bootstrap-Finish operation is performed to terminate the Bootstrap Sequence previously initiated in "Client Initiated Bootstrap" mode (or in "Server Initiated Bootstrap" mode by extension).

This operation informs the LwM2M Client, that all the Bootstrap Information have been provided by the LwM2M Bootstrap-Server.

##### Bootstrap-Discover Operation

The "Bootstrap-Discover" operation in the Bootstrap Interface is different from the "Discover" operation in the Device Management and Service Enablement interface.

The "Bootstrap-Discover" operation on the Bootstrap Interface is used to discover which LwM2M Objects and Object Instances are supported by a certain LwM2M Client. In particular, the list of Security Object Instances (ID:0) is reported, while it is not accessible in Device Management and Service Enablement Interface. If OSCORE is supported on the client, a list of OSCORE Objects (ID:21) is also reported, since this is not reported in Device Management and Service Enablement Interface either. This operation is useful to clean-up or to update an LwM2M Client configuration (e.g. adding (removing) an LwM2M Server Account to (from) the LwM2M Client configuration).

The returned payload is a list of application/link-format CoRE Links \[RFC6690\] containing the LwM2M Enabler Version and for each targeted Object - in addition to the Object Version, see Section [Object Versioning]() and [Table &lt;PROPERTIES&gt; Class Attributes]() - a sub-list of the Instances of such an Object Instance. In order to fully identify the Server Accounts supported by the Client, each element of the Instances list of the Security Object (Object ID:0) includes the associated Short Server ID and LwM2M Server URI in its parameters list while the elements of the Instances list of the Server Object (Object ID:1) also report the associated Short Server ID in their parameters list. If the LwM2M Client supports OSCORE, each element of the Instances list of the OSCORE Object (Object ID:21) includes the associated Short Server ID in its parameters list, except the OSCORE Object Instance which is associated with LwM2M Bootstrap-Server.

The Bootstrap-Server Security Object Instance does not include a Short Server ID in its parameter list (none is defined); therefore the LwM2M Server URI for the Bootstrap Server can also be omitted in such a parameters list.  

In "Bootstrap-Discover" operation the targeted path '/' is accepted in place of the Object ID, for informing the Client to report all existing Object Instances.

The "Bootstrap-Discover" operation has the following parameters:

<table>
    <caption>Bootstrap-Discover Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Object. (/ means all Objects )</td>
        </tr>
    </tbody>
</table>

For example:

* when the "Bootstrap-Discover" operation targets an Object with Object ID of 0 (Security Object), the response to the operation could be:
  
  &lt;/&gt;;lwm2m=1.1,&lt;/0/0&gt;;ssid=101;uri="coaps://server_1.example.com", &lt;/0/1/&gt;, &lt;/0/2&gt;;ssid=102;uri="coaps://server_2.example.com"

  with the meaning three LwM2M Servers are supported in that Client (which support the LwM2M Enabler in version 1.1), while the Instance ID:1 of the Security Object ID:0 contains the credentials for the LwM2M Bootstrap-Server.

* when the "Bootstrap-Discover" operation targets an Object with '/' the response to the operation could be:
  
  &lt;/&gt;;lwm2m=1.1,&lt;/0/0&gt;;ssid=101;uri="coaps://server_1.example.com", &lt;/0/1&gt;, &lt;/1/0/&gt;;ssid=101, &lt;/3/0&gt;,&lt;/5&gt;,&lt;/4&gt;

  with the meaning the Client is supporting (in LwM2M version 1.1) a Bootstrap-Server Account (/0/1), a Server Account (/0/0, /1/0) with a Short Server ID=101, A Device Object Instance (/3/0) and two other Objects, which are not instantiated yet (Firmware Update /5, and Connectivity Monitory Object /4).
  
* when the "Bootstrap-Discover" addresses an LwM2M Client supporting the LwM2M Enabler in release 1.1, and containing a configuration with Objects with Object ID of 0 (Security Object) and Object ID of 21 (OSCORE Object):

  &lt;/&gt;;lwm2m=1.1,&lt;/0/0&gt;;ssid=101;uri="coaps://server_1.example.com",&lt;/0/2&gt;;ssid=102;uri="coap://server_1.example.com",&lt;/21/0&gt;;ssid=101,&lt;/21/2&gt;;ssid=102,&lt;/0/1&gt;,&lt;/21/1/&gt;

  with the meaning two LwM2M Servers are supported in that Client (that supports the LwM2M Enabler in version 1.1), the Instance ID:0 of the Security Object ID:0 and the Instance ID:0 of the OSCORE Object ID:21 contains the DTLS and OSCORE credentials, respectively, of the LwM2M Server with ssid=101. The instance ID:2 of the OSCORE Object ID:21 contains the OSCORE credentials of the LWM2M Server with ssid=102, which supports No_Sec mode. The Instance ID:1 of the OSCORE Object ID:21 contains the OSCORE credentials for the LwM2M Bootstrap-Server.

* when the "Bootstrap-Discover" addresses an LwM2M Client supporting the LwM2M Enabler in release 1.1, and containing a configuration with an hypothetical LwM2M Object ID:55 in Version 1.9, with one Instance (/55/0):
  
  &lt;/&gt;;lwm2m=1.1,&lt;/0/0&gt;,&lt;/0/1&gt;;ssid=101;uri="coaps://server_1.example.com", &lt;/1/0/&gt;;ssid=101, &lt;/3/0&gt;,&lt;/5&gt;,&lt;/4&gt;,&lt;/55&gt;;ver=1.9,&lt;/55/0&gt;
  
  Note: In previous versions of this document, the LwM2M Enabler Version link parameter was not associated to any URI-Reference in the examples (e.g. "lwm2m=1.0,</0/0>;ssid=101,</0/1/>,</0/2>;ssid=102"). Thus, the provided examples were not in conformance with the  ABNF of \[RFC6690\]. LwM2M Servers MAY accept this particular error in the LwM2M Client's response to the "Bootstrap-Discover" operation.
  
##### Bootstrap-Read Operation

The "Bootstrap-Read" operation in the Bootstrap Interface is a restricted form of the "Read" operation found in the Device Management and Service Enablement interface, and MUST be limited to target Objects that are strictly necessary to setup a proper configuration in an LwM2M Client. 

In this specification the only acceptable targets for the "Bootstrap-Read" operation is the LwM2M Server Object (Object ID: 1) and the Access Control Object (Object ID:2). This operation will allow the Bootstrap-Server to query the existing Server Account(s) to determine validity and to add new Server Account(s) without breaking the access control rights already in place in the targeted LwM2M Client.

The "Bootstrap-Read" operation is used to access a single Instance or all Instances of the Server Object (ID:1) and the Access Control Object (ID:2). 

{:page-break}

The "Bootstrap-Read" operation has the following parameters:
<table>
    <caption>Bootstrap-Read Parameters</caption>
 <thead>
  <th> Parameter </th>
  <th> Required </th>
  <th> <strong> Default Value </th>
  <th> <strong> Notes </th>
 </thead>
 <tbody>   
 <tr>
   <td> Object ID </td>
   <td> Yes </td>
   <td> - </td>
   <td> Indicates the Object. Object ID MUST be '1' (Server Object) or '2' (Access Control Object). An error is reported otherwise.</td>
 </tr>
  <tr>
   <td> Object Instance ID </td>
   <td> No </td>
   <td> - </td>
   <td> Indicates the Object Instance to be read. <br\> If no Object Instance ID is indicated, then all Instances of the targeted Object are returned.</td>
 </tr>
    </tbody>    
</table> 

As a simple illustration based on the second example of Section [Multiple Object Instance Request Examples]():
the "Bootstrap-Read /2" operation with JSON requested format could provide the following answer:

<table>
    <caption>Bootstrap-Read Example with Multiple Object Instances</caption>
 <tr>
  <td>
  [{"bn":"/2/","n":"0/0","v":1},<br>
   {"n":"0/1","v":0},<br>
   {"n":"0/2/127","v":7},<br>
   {"n":"0/3","v":127},<br>
   {"n":"2/0","v":3},<br>
   {"n":"2/1","v":0},<br>
   {"n":"2/2/127","v":7},<br>
   {"n":"2/2/310","v":7},<br>
   {"n":"2/3","v":127}]<br>
  </td>
 </tr>
</table>

Any optional resources included in the "Bootstrap-Read" operation response that are not supported by, or unknown to, the LwM2M Bootstrap-Server MUST NOT be interpreted as an error by the LwM2M Bootstrap-Server.

##### Bootstrap-Write Operation

The "Bootstrap-Write" operation in Bootstrap Interface is different from the "Write" Operation in the Device Management and Service Enablement interface. The LwM2M Client MUST write the value included in the payload regardless of an existence of the targeted Object Instance(s) or Resource(s).

Any optional Resources included in the "Bootstrap-Write" operation targeting an Object or an Object Instance that are not supported by, or unknown to, the LwM2M Client MUST NOT be interpreted as an error by the LwM2M Client. If the LwM2M Client supports optional resources not present in the payload, it MUST NOT instantiate these optional resources.

The "Bootstrap-Write" operation can be sent multiple times.

Only in the Bootstrap Interface, the "Bootstrap-Write" MAY target just an Object ID, which will allow a Bootstrap-Server in using a TLV, LwM2M CBOR, SenML CBOR or SenML JSON formatted payload, to populate an LwM2M Client in a single message containing several Instances of the same Object.

{:page-break}

The "Bootstrap-Write" operation has the following parameters:

<table>
    <caption>"Bootstrap-Write" Parameters</caption>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>Required</th>
        <th>Default Value</th>
        <th>Notes</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Object ID</td>
        <td>Yes</td>
        <td>-</td>
        <td>Indicates the Object.</td>
    </tr>
    <tr>
        <td>Object Instance ID</td>
        <td>No</td>
        <td>-</td>
        <td>Indicates the Object Instance to write.<br>
            If no Object Instance ID is indicated, Object Instance(s) MUST be specified in the TLV, LwM2M CBOR, SenML CBOR or SenML JSON payload.</td>
    </tr>
    <tr>
        <td>Resource ID</td>
        <td>No</td>
        <td>-</td>
        <td>Indicates the Resource to write. The payload is the new value for the Resource.<br> 
            If no Resource ID is indicated, then the value included payload is an Object Instance containing the Resource values.</td>
    </tr>
    <tr>
        <td>New Value</td>
        <td>Yes</td>
        <td>-</td>
        <td>The new value included in the payload to update the Object Instance(s) or Resource</td>
    </tr>
    </tbody>
</table>

##### Bootstrap-Delete Operation

The "Bootstrap-Delete" operation targets one or several Object Instances and can be sent multiple times.

Only in the Bootstrap Interface, the "Bootstrap-Delete" operation MAY target any Instance or all Instances of any Object including the Security Object (ID:0), supported by the LwM2M Client. The two exceptions are the LwM2M Bootstrap-Server Account, potentially including an associated Instance of an OSCORE Object ID:21, and the single Instance of the mandatory Device Object (ID:3), which are not affected by any Delete operation.

When the "Bootstrap-Delete" operation is used without any parameter (i.e. without Object ID parameter), all Instances of all Objects in the LwM2M Client MUST be removed (except for the two cases mentioned above). This functionality could be used for initialization purposes before LwM2M Bootstrap-Server sends Write operation(s) to the LwM2M Client.

The "Bootstrap-Delete" operation has the following parameters:

<table>
    <caption>Bootstrap-Delete Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Object from which Object Instance will be deleted. If no Object ID is indicated, all existing Object Instances (except the LwM2M Bootstrap-Server Account, potentially including an associated Instance of an OSCORE Object, and the Instance of the Device Object) in the LwM2M Client will be deleted.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Object Instance to delete. If no Object Instance ID is indicated, then all Instances of the designated Object (Object ID MUST be provided) are deleted.</td>
        </tr>
    </tbody>
</table>

##### Bootstrap-Pack-Request Operation

The "Bootstrap-Pack-Request" operation is only performed to initiate the Bootstrap Sequence in the "Client Initiated Bootstrap" mode by the client indicating that the client wants to retrieve a "Bootstrap-Pack".

"Bootstrap-Pack" contains, at minimum, the required bootstrap information defined in Section [Bootstrap Information](). Only by using "Bootstrap-Pack" in the Bootstrap Interface, an LwM2M client can be populated in a single message containing several Objects and several Instances of such Objects.

In "Bootstrap-Pack-Request" operation, the Bootstrap Server receives a "Bootstrap-Pack-Request" and the Bootstrap Server responds with a "Bootstrap-Pack" which the client uses to create or replace objects on the client. 

The LwM2M client MUST delete the existing Objects and their Instances in the client with the Objects and their Instances given in the "Bootstrap-Pack" if the Object IDs are the same. Object IDs available in the LwM2M Client which are not provided in the "Bootstrap-Pack" MUST NOT be deleted. The two exceptions are the LwM2M Bootstrap-Server Account, potentially including an associated Instance of an OSCORE Object ID:21, and the single Instance of the mandatory Device Object (ID:3), which are not affected by any Delete operation.

The LwM2M Client MUST write the value included in the "Bootstrap-Pack" payload regardless of a previous existence of the targeted Object Instance(s) or Resource(s). Any optional Resources included in the "Bootstrap-Pack" targeting an Object or an Object Instance that are not supported by, or unknown to, the LwM2M Client MUST NOT be interpreted as an error by the LwM2M Client. If the LwM2M Client supports optional resources not present in the payload, it MUST NOT instantiate these optional resources.

If the LwM2M Bootstrap-Server does not support "Bootstrap-Pack-Request", it MUST return an error code indicating not implemented to the LwM2M Client when "Bootstrap-Pack-Request" is received. If the LwM2M Server supports the "Bootstrap-Pack-Request" but wishes the LwM2M Client not to use "Bootstrap-Pack" for bootstrapping, it MUST return an error code indicating that the method is not allowed to the LwM2M Client. After receiving an error in response to a "Bootstrap-Pack-Request", the LwM2M Client MUST use "Bootstrap-Request" operation to continue Client Initiated Bootstrap.

If the LwM2M Client does not receive any response from the LwM2M Bootstrap-Server during the EXCHANGE\_LIFETIME time period, the LwM2M Client MAY retry bootstrapping with "Bootstrap-Pack-Request".

The "Bootstrap-Pack-Request" operation has the following parameters:

<table>
    <caption>Bootstrap-Pack-Request Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Endpoint Client Name</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the LwM2M Client's "Endpoint Client Name". This parameter is optional if it is equal to the identifier in the security protocol and deployment is such that the security protocol identifier is always available for the server (e.g. no proxies in between).</td>
        </tr>
    </tbody>
</table>


As a simple illustration based on the LwM2M Client example defined in Section [Example LwM2M Client (Informative)](), a Bootstrap-Pack could look like the following in SenML JSON encoded format below. For editorial purposes a line breaks has been added.

<table>
    <caption>Bootstrap-Pack Example with Multiple Objects and Multiple Object Instances</caption>
 <tr>
  <td>
	[{"bn":"/0/1/", "n":"0","vs":"coaps://server1.example.com"},<br>
	{"n":"1","vb":false},<br>
	{"n":"2","v":0},<br>
	{"n":"3","vd":"YjMxM2NjMjItZjk2OS00MmVjLWFkNDI"},<br>
	{"n":"4","vd":""},<br>
	{"n":"5","vd":"HKICjXGXx3jprvXvaQgr6g"},<br>
	{"n":"10","v":101},<br>
	{"bn":"/0/2/", "n":"0","vs":"coaps://server2.example.com",<br>
	"n":"1","vb":false},<br>
	{"n":"2","v":1},<br>
	{"n":"3","vd":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEoJ3LG8c55/Ga+prcsZRJaL+6c+/
	               OwptQSG60TRspwZNEmXCjc2gwyyvV1+wF0r0fwHtt9eSLVM53pqcinDqRwg"},<br>
	{"n":"4","vd":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEgsdz83jTDCeDpI64Ebls9qkGlKh
	               WTx5/bTZhUvEWmJUPb3xAzaWFM0+Dd1ChAvW/JVCM655V38DxKkVRmaTJYA"},<br>
	{"n":"5","vd":"MHcCAQEEIJ81LaFklXSOFG/LU3C46W0pLO1VZ6j65Voiu2fZFlG4oAoGCCqGSM4
	               9AwEHoUQDQgAEoJ3LG8c55/Ga+prcsZRJaL+6c+/OwptQSG60TRspwZNEmXCjc2
	               gwyyvV1+wF0r0fwHtt9eSLVM53pqcinDqRwg"},<br>
	{"n":"10","v":102},<br>
	{"bn":"/1/0/", "n":"0","v":101},<br>
	{"n":"1","v":86400},<br>
	{"n":"2","v":300},<br>
	{"n":"3","v":6000},<br>
	{"n":"5","v":86400},<br>
	{"n":"6","vb":true},<br>
	{"n":"7","vs":"U"},<br>
	{"bn":"/1/1/", "n":"0","v":102},<br>
	{"n":"1","v":86400},<br>
	{"n":"2","v":60},<br>
	{"n":"3","v":6000},<br>
	{"n":"5","v":86400},<br>
	{"n":"6","vb":false},<br>
	{"n":"7","vs":"U"},<br>
	{"bn":"/2/0/", "n":"0","v":1},<br>
	{"n":"1","v":0},<br>
	{"n":"2/101","v":15},<br>
	{"n":"3","v":101},<br>
	{"bn":"/2/1/", "n":"0","v":1},<br>
	{"n":"1","v":1},<br>
	{"n":"2/102","v":15},<br>
	{"n":"3","v":102}]<br>
  </td>
 </tr>
</table>

### Client Registration Interface

The LwM2M Server MUST support all operations in this interface. The LwM2M Client MUST support the "Register" and the "Update" operations. The LwM2M Client SHOULD support the "De-register" operation.

The Client Registration Interface is used by an LwM2M Client to register with one or more LwM2M Servers, maintain each registration, and de-register from an LwM2M Server. The registration is based on the Resource Model and Identifiers defined in Section [Identifiers and Resources](). When registering, the LwM2M Client performs the "Register" operation and provides the information required by the LwM2M Server (e.g. the supported Objects and existing Object Instances) as well as optional parameters (e.g. Endpoint Client Name). The LwM2M Client and the LwM2M Server maintains the LwM2M Registration Session based upon the configured parameters (e.g. Lifetime, security context). The ability to maintain an LwM2M Registration Session may be impacted by a change in the Transport Session, e.g. a binding change.

The LwM2M Client periodically performs an update of its registration information to the registered LwM2M Server(s) by performing the "Update" operation.

If the lifetime of a registration expires without receiving an update from the LwM2M Client the LwM2M Server will consider it a de-registration:

* The LwM2M Server MUST remove the registration of that LwM2M Client and existing observations. If the LwM2M Client is unaware of the expiration, when the LwM2M Client performs a registration update the LwM2M Server will respond with an error.  

* Upon receipt of the error message, the LwM2M Client SHOULD reset its state and register again. The LwM2M Client MUST re-register ("Update" is not sufficient) to the LwM2M Server in order to be connected again, before initiating any further communication.

If the LwM2M Server or the LwM2M Client set a value to the Lifetime Resource of the Server Object Instance, this value becomes the new lifetime of the Registration.

During "Register" or "Update" operations, the parameter Lifetime – if present – MUST match the current value of the Mandatory Lifetime Resource of the LwM2M Server Object Instance.

Finally, when shutting down or discontinuing use of an LwM2M Server, the LwM2M Client performs a "De-register" operation.

The Binding Resource of the LwM2M Server Object informs the LwM2M Client about the transport protocol preferences of the LwM2M Server for the Transport Session between the LwM2M Client and LwM2M Server. The LwM2M Client SHOULD perform the operations with the modes indicated by the Binding Resource of the LwM2M Server Object Instance.

<figure class="text-center">
      <img src="images/client_registration_interface_example_flows.svg" alt="Client Registration Interface example flows">
      <figcaption>Client Registration Interface example flows</figcaption>
</figure>

The mapping to underlying transports is detailed in \[LwM2M-TRANSPORT\]. 

#### Register Operation

Registration is performed when an LwM2M Client sends a "Register" operation to the LwM2M Server. After the LwM2M Device is turned on and the bootstrap procedure has been completed, the LwM2M Client MUST perform a "Register" operation to each LwM2M Server that the LwM2M Client has a Server Object Instance. [Table Registration Parameters]() describes the parameters used for the "Register" operation.

The "Register" operation SHOULD include the Endpoint Client Name parameter along with other parameters listed in [Table Registration Parameters](). When the Endpoint Client Name parameter is provided in the "Register" operation then it MUST contain a value for the Endpoint Client Name parameter that is unique on that LwM2M Server.

Upon receiving a "Register" operation from the LwM2M Client, the LwM2M Server records the connection information of the registration message (e.g. source IP address and port or MSISDN) and uses this information for all future interactions with that LwM2M Client.

If the LwM2M Client sends a "Register" operation to the LwM2M Server even though the LwM2M Server has registration information of the LwM2M Client, the LwM2M Server removes the existing registration information and performs the new "Register" operation. This situation happens when the LwM2M Client forgets the state of the LwM2M Server (e.g. factory reset).

The LwM2M Server MUST support all the parameters and payloads listed at [Table Registration Parameters](), except for the Profile ID. The LwM2M Client MUST implement LwM2M Version, Lifetime, Object and Object Instances and MAY implement all other parameters.

<table>
    <caption>Registration Parameters</caption>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>Required</th>
        <th>Default Value</th>
        <th>Notes</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Endpoint Client Name</td>
        <td>No</td>
        <td></td>
        <td>See Section <a href="">Identifiers</a></td>
    </tr>
    <tr>
        <td>Lifetime</td>
        <td>Yes</td>
        <td></td>
        <td>Indicates the expected lifetime of the registration for this LwM2M client. This value MUST be the same as the value held in the Resource named "Lifetime" of the corresponding instance of Server Object (ID \#1): /1/x/1.</td>
    </tr>
    <tr>
        <td>LwM2M Version</td>
        <td>Yes</td>
        <td></td>
        <td>Indicates the version of the LwM2M Enabler that the LwM2M Client supports. The LwM2M version number reported MUST correspond to the approved version number of this document.</td>
    </tr>
    <tr>
        <td>Binding Mode</td>
        <td>No</td>
        <td>U</td>
        <td>Indicates the supported binding modes in the LwM2M Client. This value SHOULD be the same as the value in the “Supported Binding and Modes” resource in the Device Object (/3/0/16). The valid values of the parameter are listed in Section <a href="">Behaviour with Current Transport Binding and Modes</a></td>
    </tr> 
    <tr>
        <td>Queue Mode</td>
        <td>No</td>
        <td></td>
        <td>Indicates whether Queue Mode is supported. The Queue Mode is useful when the LwM2M Device is not reachable by the LwM2M Server at all times and it helps the LwM2M Client to reduce power consumption by sleeping longer.
</td>
    </tr> 
    <tr>
        <td>SMS Number</td>
        <td>No</td>
        <td></td>
        <td>The value of this parameter is the MSISDN or External Identifier where the LwM2M Client can be reached for use with the SMS binding or when both the LwM2M Client and the LwM2M Server support the SMS registration update trigger mechanism defined in [LwM2M-TRANSPORT].</td>
    </tr> 
    <tr>
        <td>Objects and Object Instances</td>
        <td>No</td>
        <td></td>
        <td>A list of Objects supported and Object Instances available on the LwM2M Client (Security Object ID:0, and OSCORE Object ID:21, if present, MUST NOT be part of this list).</td>
    </tr>
    <tr>
        <td>Profile ID</td>
        <td>No</td>
        <td></td>
        <td>The Profile ID parameter represents a list of Objects supported and Object Instances available on the LwM2M Client (Security Object ID:0, and OSCORE Object ID:21, if present, MUST NOT be part of this list) by reference rather than by value. Multiple Profile IDs MAY be included. The Profile ID argument value MUST be encoded as an ASCII string following the ABNF below.</td>
    </tr>
  </tbody>
</table>

The syntax of the "Profile ID" argument value is as follows:

```
value = profileID / ( """ profileID *( "," profileID ) """ )
profileID = dynamicID / preConfigID
dynamicID = suite-identifier ":" 1*(ahlc)
suite-identifier = 1*( DIGIT )
ahlc = DIGIT / "a" / "b" / "c" / "d" / "e" / "f"
preConfigID = ("oma" / "v") ":" 1*(ALPHA / DIGIT / "-")
```

The Profile ID can be used in two different deployment modes, namely 

- In the pre-configured mode the identifier used in the Profile ID refers to a list of Objects supported and Object Instances available on the LwM2M Client (Security Object ID:0, and OSCORE Object ID:21, if present, MUST NOT be part of this list). The value is either registered with OMNA or a vendor-specific value. The value needs to be pre-configured on the LwM2M Client and on the LwM2M Server so that both communication peers understand how to map the Profile ID value to the list of Objects and Object Instances it represents. 

- In the dynamically generated mode the LwM2M Client itself creates a fingerprint (in form of a cryptographic hash) of a list of Objects supported and Object Instances available on the LwM2M Client (Security Object ID:0, and OSCORE Object ID:21, if present, MUST NOT be part of this list) it wants to convey with the register operation to the LwM2M Server. The LwM2M Client then puts this fingerprint value into the Profile ID parameter. To avoid collisions, the selected hash algorithm needs to be sufficiently long, i.e. 32 bits and longer. 

If the LwM2M Server cannot retrieve the list of Objects and Object Instances based on the received Profile ID value it MUST reply to the registration message with an error code. The LwM2M Client MUST then perform the register operation with a registration message that MUST include the list of Objects supported and Object Instances available on the LwM2M Client. 

Using the dynamically generated mode the LwM2M Server may be able to determine the mappings between the Profile ID value and its corresponding list of Objects and Object Instances. 

An LwM2M Client MAY include multiple Profile ID parameters in a single message and MAY mix the Profile ID parameter with a list of Objects and Object Instances in the payload of the message. The latter allows the LwM2M Client to use the Profile ID for a commonly used combination of Objects and Object Instances while offering the possibility to include rarely used configurations in the payload. 

The LwM2M Server uses all provided Profile ID values and the provided Objects and Object Instances to determine the list of supported Objects and Object Instances of the LwM2M Client. If no information is provided in the registration request the LwM2M Server MAY determine the list of supported Objects and Object Instances of the LwM2M Client through pre-configuration, which is outside the scope of this specification. If the LwM2M Server cannot determine the list of Objects and Object Instances it MUST reply to the registration message with an error code.

The value used in the Profile ID follows a naming convention: 

- For hashes this specification uses the numerical ID value of IANA registered Named Information Hash Algorithms defined by \[RFC6920\] to indicate the hash algorithms used. For example, the use of SHA256 truncated to 32 bits is indicated by the profile ID value "6:1234abcd".

- For values used in application domains registered via the Open Mobile Naming Authority (OMNA), the prefix is "oma:" followed by the registered value. The list of standardized values can be found at \[OMNA\].

- For values used in vendor-specific deployments, the prefix "v:" followed by the value is used. 

An LwM2M Server MUST refuse a Client's Registration request, if it does not support the LwM2M Enabler version indicated by the Client.

An LwM2M Server MAY refuse to use the Profile ID by returning an error requiring the LwM2M to indicate the list of Objects and Object Instances in a subsequent registration message.

When an Object defined outside of an LwM2M Enabler has to be registered by the Client, but is not supported by the Server (unknown Object or unsupported Object version) it MUST NOT be interpreted as an error by the Server and will not prevent the Client's Registration request to be accepted.

The Media-Type of the registration message, if used, MUST be the CoRE Link Format (application/link-format) defined in \[RFC6690\], so that each Object is described as a Link according to that format. The Target component of the link is required, and consists of the Object path and Object Version CoRE link parameter "ver" if required as it is defined in Section [Object Versioning]() of this document. Any other parameters included in the link MUST NOT be interpreted as an error, unless specified for use by the LwM2M Enabler.

As an example, the payload for an LwM2M Client supporting LwM2M Server, Access Control, Device, Connectivity Monitoring and Firmware Update Objects from Section [LwM2M Objects defined by OMA (Normative)]() would be (for the example client of Section [Example LwM2M Client (Informative)]()):

&lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/2/0&gt;,&lt;/2/1&gt;,&lt;/2/2&gt;,&lt;/2/3&gt;,&lt;/2/4&gt;,&lt;/3/0&gt;,&lt;/4/0&gt;,&lt;/5&gt;

If the LwM2M Client supports optional data formats, it MAY inform the LwM2M Server by including the content types in the root path link using the `ct=` link attribute defined in \[CoAP\]. An example is as follows (note that the content type value 110 is the value assigned in the CoAP Content-Format Registry for the SenML JSON format used by LwM2M).

&lt;/&gt;;ct=110, &lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/2/0&gt;,&lt;/2/1&gt;,&lt;/2/2&gt;,&lt;/2/3&gt;,&lt;/2/4&gt;,&lt;/3/0&gt;,&lt;/4/0&gt;,&lt;/5&gt;

Another example if the LwM2M Client supports the SenML JSON format, the CBOR format, and the SenML CBOR format:

&lt;/&gt;;ct="110 112 60", &lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/2/0&gt;,&lt;/2/1&gt;,&lt;/2/2&gt;,&lt;/2/3&gt;,&lt;/2/4&gt;,&lt;/3/0&gt;,&lt;/4/0&gt;,&lt;/5&gt;


##### Bootstrap and LwM2M Server Registration Mechanisms

In order to provide robust mechanisms for LwM2M Server registrations, resources have been defined in the LwM2M Server Object to configure the order of LwM2M Server registrations, registration retry behavior and the ability for the LwM2M Client to react during registration failure conditions. These resources are optional, so the behavior is only enabled when these resources are defined. If these resources are not defined, default values in [Table Registration Procedures Default Values]() or a manufacturer defined implementation may be used.

The first step is for the LwM2M Client to determine the registration order when multiple LwM2M Servers are defined (i.e. multiple  instances of LwM2M Server Objects). The LwM2M Client orders the LwM2M Server registrations in ascending order of the "Registration Priority Order" value. It is recommended that each ordered LwM2M Server has a unique priority, so it is implementation dependent how to order those LwM2M Servers with the same priority. If this value is not defined for an LwM2M Server, registration attempts to that LwM2M Server are managed independently and do not impact other LwM2M Server registrations.

For each LwM2M Server that is defined in the registration order, the "Registration Failure Block" resource indicates the behavior of the LwM2M Client upon registration failure to that LwM2M Server. When the "Registration Failure Block" value is set to true and registration to the LwM2M server fails, the LwM2M Client performs additional registration retry sequences and blocks registration to other LwM2M Servers in the priority order. When the "Registration Failure Block" value is set to false, the LwM2M Client proceeds with registration to the next LwM2M Server in the priority order whether the current LwM2M Server is successfully registered or not.

The procedure to manage the registration to LwM2M Servers that have a "Registration Priority Order" resource included is defined here:

<figure>
      <img src="images/OrderedServersProcedure.svg" alt="Ordered Servers Procedure">
      <figcaption>Ordered Servers Procedure</figcaption>
</figure>

When registration fails to non-blocking LwM2M Servers in the "Ordered Servers Procedure", it is not specified how the LwM2M Client retries registration with those LwM2M Servers. One solution could be to execute the "Single Unordered Servers Procedure" for all failed non-blocking LwM2M Servers.

The "Communication Retry Count", "Communication Retry Timer", "Communication Sequence Delay Timer" and "Communication Sequence Retry Count" resources indicate to the LwM2M Client the retry mechanism to be used for registration attempts to a single LwM2M Server. The registration mechanism to an LwM2M Server consists of a sequence of "Communication Retry Count" attempts within a retry sequence. The "Communication Retry Timer" value is multiplied by two to the power of the current attempt minus one (2^(Current Attempt-1)) to create an exponential back-off between attempts within a single retry sequence to an LwM2M Server. If one retry sequence of attempts to an LwM2M Server fails, then a new sequence of attempts may be retried after "Communication Sequence Delay Timer." The maximum number of retry sequences to an LwM2M Server is set by the "Communication Sequence Retry Count."

How these values are applied to those LwM2M Servers that are part of the ordered registration is defined in the "Single Ordered Server Procedure" here:

<figure>
      <img src="images/SingleOrderedServerProcedure.svg" alt="Single Ordered Server Procedure">
      <figcaption>Single Ordered Server Procedure</figcaption>
</figure>

How these values are applied to those LwM2M Servers that are NOT part of the ordered registration is defined in the "Single Unordered Server Procedure" here:

<figure>
      <img src="images/SingleUnorderedServerProcedure.svg" alt="Single Unordered Server Procedure">
      <figcaption>Single Unordered Server Procedure</figcaption>
</figure>

Note: Current Attempt and Current Sequence start at 1 to represent the first attempt or sequence in the "Single Ordered Server Procedure" and "Single Unordered Server Procedure". These values should be reset to 1 at the start of each sequence and between sequences.

The "Initial Registration Delay Timer" defines the delay before the single registration procedure (ordered or unordered) is attempted for an LwM2M Server.

The "Bootstrap on Registration Failure" resource indicates to the LwM2M Client whether to re-bootstrap in case of a registration failure to the LwM2M Server. The exact behavior in case of bootstrap registration success, triggered by a server registration failure, is implementation dependent. For example, already successful LwM2M Server registrations may be maintained.

Note: It is recommended to set the "Bootstrap on Registration Failure" resource to true only when "Registration Failure Block" is set to true for any ordered LwM2M Server (i.e. that LwM2M Server is critical) to avoid a situation where the device has no recovery method. On the other hand, if the “ Bootstrap on Registration Failure” resource is set to false, it is recommended to set the “Registration Failure Block” resource to false for an ordered LwM2M Server.”

Note: It is recommended to set the "Communication Sequence Retry Timer" resource sufficiently large to accommodate for an entire registration attempt sequence to avoid an immediate retry sequence.

The registration retry mechanisms for the Bootstrap Server are implementation dependent.

The following table represents the recommended default values to use when the resources are not defined in the LwM2M Server Object:

<table>
        <caption>Registration Procedures Default Values</caption>
        <thead>
        <tr>
            <th>Resource</th>
            <th>Default Value</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>Registration Priority Order</td>
            <td>Not defined</td>
        </tr>
        <tr>
            <td>Registration Failure Block</td>
            <td>False</td>
        </tr>
        <tr>
            <td>Initial Registration Delay Timer</td>
            <td>0 (seconds)</td>
        </tr>
        <tr>
            <td>Bootstrap on Registration Failure</td>
            <td>True</td>
        </tr>
        <tr>
            <td>Communication Retry Count</td>
            <td>5</td>
        </tr>
        <tr>
            <td>Communication Retry Timer</td>
            <td>1 (minute)</td>
        </tr>
        <tr>
            <td>Communication Sequence Delay Timer</td>
            <td>24 (hours)</td>
        </tr>
        <tr>
            <td>Communication Sequence Retry Count</td>
            <td>1</td>
        </tr>
        </tbody>
</table>


##### Behaviour with Current Transport Binding and Modes

Behaviour of the LwM2M Server and the LwM2M Client is differentiated by Current Transport Binding and Modes. Current Transport Bindings are decided by "Binding" Resource set by the LwM2M Server. The "Binding" resource contains a combination of supported transports, for example UDP and TCP.

[Table Behaviour with Current Transport Bindings]() describes the behaviour of the LwM2M Server and the LwM2M Client for each Current Transport Bindings.

<table>
        <caption>Behaviour with Current Transport Bindings</caption>
        <thead>
        <tr>
            <th>Current Transport Bindings</th>
            <th>Behaviour</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>U (UDP)</td>
            <td><p>The LwM2M Server expects that the LwM2M Client is reachable via the UDP binding at any time.</p>
                <p>The LwM2M Server MUST send requests to an LwM2M Client using the UDP binding. The LwM2M Client MUST send the response to such a request over the UDP binding.</p>
                <p>This is the normal default mode of operation.</p>
            </td>
        </tr>
        <tr>
            <td>M (MQTT)</td>
            <td><p>The LwM2M Server expects that the LwM2M Client is reachable via the MQTT binding at any time.</p>
                <p>The LwM2M Server MUST send requests to an LwM2M Client using the MQTT binding. The LwM2M Client MUST send the response to such a request over the MQTT binding.</p>
            </td>
        </tr>
        <tr>
            <td>H (HTTP)</td>
            <td><p>The LwM2M Server expects that the LwM2M Client is reachable via the HTTP binding at any time.</p>
                <p>The LwM2M Server MUST send requests to an LwM2M Client using the HTTP binding. The LwM2M Client MUST send the response to such a request over the HTTP binding.</p>
            </td>
        </tr>		
        <tr>
            <td>T (TCP)</td>
            <td><p>The LwM2M Server expects that the LwM2M Client is reachable via the TCP binding at any time.</p>
                <p>The LwM2M Server MUST send requests to an LwM2M Client using the TCP binding. The LwM2M Client MUST send the response to such a request over the TCP binding.</p>
        </td>
        </tr>
        <tr>
            <td>S (SMS)</td>
            <td><p>The LwM2M Server expects that the LwM2M Client is reachable via the SMS binding at any time.</p>
                <p>The LwM2M Server MUST send requests to an LwM2M Client using the SMS binding. The LwM2M Client MUST send the response to such a request over the SMS binding.</p>
            </td>
        </tr>
        <tr>
            <td>N (Non-IP)</td>
            <td><p>Non-IP is defined in accordance with \[3GPP 23.401\] and is applicable for both NB-IoT and LTE M networks.  Appendix C in \[LwM2M-TRANSPORT\]: LWM2M over 3GPP LPWA Networks - NB-IoT and LTE M, describes in detail the alternate routes for delivering non-IP data. Non-IP can also refer to alternate transports such as LoRaWAN</p> 
                <p>The LwM2M Server MUST send requests to an LwM2M Client using the Non-IP binding. The LwM2M Client MUST send the response to such a request over the Non-IP binding.</p>
            </td>
        </tr>
    </tbody>
</table>

* While multiple transports are supported, only one transport binding can be used during the entire Transport Session. As an example, when UDP and SMS are both supported, the LwM2M Client and the LwM2M Server can choose to communicate either over UDP or SMS during the entire Transport Session.<br>

* "Preferred Transport" is an optional resource in the LwM2M Server Object (/1/x/22). If this resource is defined, the client SHALL use this to initiate a connection over the specified transport, unless unable to do so. If this resource is not defined, the client SHALL use a client-preferred binding supported by both the server (from the list in the "binding" resource of the LwM2M server object - /1/x/7) and client (from the list in "Supported Binding and Modes" resource in the Device object - /3/x/16). The "Preferred Transport" resource can also be used to select a required transport. For example, when Non-IP is normally indicated as preferred, this resource can be set to UDP temporarily to perform a firmware update.

* "Registration Update Trigger" is a mandatory resource in the LwM2M Server Object (/1/x/8). The client SHALL use the argument when the "Registration Update Trigger" resource is executed unless not supported by the client or not indicated as supported by the server in the "binding" resource of the LwM2M Server Object (/1/x/7). When that argument indicates an overriding binding that is supported by the client, the client SHALL immediately release the existing transport connection and establish a new transport connection using the overriding binding if that overriding binding is different than the current transport connection.

* The client SHALL assume that the server supports the UDP binding even if the server does not include UDP (“U”) in the "binding" resource of the LwM2M server object (/1/x/7).

* When the APN Connection Profile object is defined with a "PDN Type" resource (/11/x/24), that "PDN Type" SHALL be preferred when present in the "binding" resource of the LwM2M server object (/1/x/7).

* When configurations related to the bindings change, those new values SHALL NOT affect the current Transport Session, and the new values SHALL be applied to the future Transport Sessions. The existing LwM2M client registration SHALL NOT be affected by the use of updated bindings configuration.

* Queue Mode and device triggering can be enabled independently, and can be used in conjunction with one or more transports. Using the device triggering, the LwM2M Server MAY request the LwM2M Client to perform operations, such as the "Update" operation by sending an "Execute" to the "Registration Update Trigger" Resource via SMS. An LwM2M Client is not expected to send an SMS response for a device trigger message.

#### Update Operation

Periodically or based on certain events within the LwM2M Client or initiated by the LwM2M Server, the LwM2M Client updates its registration information with an LwM2M Server by sending an "Update" operation to the LwM2M Server.

The "Update" operation can be initiated by the LwM2M Server via an "Execute" operation on the "Registration Update Trigger" Resource of the LwM2M Server Object. The LwM2M Client can perform an "Update" operation to refresh the lifetime of its registration to an LwM2M Server.

When any of the parameters listed in [Table Update Parameters]() changes, the LwM2M Client MUST send an "Update" operation to the LwM2M Server. This "Update" operation MUST contain only the parameters listed in [Table Update Parameters]() which have changed compared to the last registration parameters sent to the LwM2M Server.

{:page-break}

<table>
    <caption>Update Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Lifetime</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Binding Mode</td>
            <td>No</td>
        </tr>
        <tr>
            <td>SMS Number</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Objects and Object Instances</td>
            <td>No</td>
        </tr>
        <tr>
            <td>Profile ID</td>
            <td>No</td>
        </tr>
    </tbody>
</table>


When present, the Objects and Object Instance list and/or the Profile ID MUST follow the same rules as in the Register operation.

The payload Media-Type of that "Update" operation is the same as the one of the "Registration" operation.

When an Object defined outside of an LwM2M Enabler is part of the LwM2M Client update registration list, but is not supported by the LwM2M Server (unknown Object or unsupported Object version), it MUST NOT be interpreted as an error by this LwM2M Server and will not prevent the LwM2M Client's "Update" operation to be accepted.

Two common operations are:

1.  Extending the lifetime of a registration

In this case the LwM2M Client sends an "Update" operation with no parameters.

[Figure Update Example Flow #1]() shows an example exchange where the LwM2M Client sends an "Update" operation that only refreshes the registration, i.e. the message does not contain any parameters. With the second "Update" the Client changes the lifetime field to 6000 (seconds) and hence the lt parameter is included in the message.

<figure class="text-center">
      <img src="images/client_registration_update_example_flows_1.svg" alt="Update Example Flow #1">
      <figcaption>Update Example Flow #1</figcaption>
</figure>

2.  Adding and removing Objects and Object Instances

In this case the LwM2M Client sends an "Update" with a body listing the complete list of objects and object instances.

[Figure Update Example Flow #2]() shows an example exchange whereby the LwM2M Client starts with an initial registration of two instances for an LwM2M Object with ID 12. Later, the LwM2M Server adds a third instance and subsequently deletes the second. With the "Update" operation the LwM2M Client includes the new list of Objects and Object Instances.

<figure class="text-center">
      <img src="images/client_registration_update_example_flows_2.svg" alt="Update Example Flow #2">
      <figcaption>Update Example Flow #2</figcaption>
</figure>

#### De-register Operation

When an LwM2M Client determines that it no longer requires to be available to an LwM2M Server (e.g. LwM2M Device factory reset), the LwM2M Client SHOULD send a "De-register" operation to the LwM2M Server. Upon receiving this message, the LwM2M Server removes the registration information from the LwM2M Server.

### Device Management and Service Enablement Interface

The LwM2M Server and the LwM2M Client MUST support all the operations on this interface unless clearly stated otherwise. Support for some of the non-mandatory operations may also be dependent on the choice of transport layer and the services it provides.

The Device Management and Service Enablement Interface is used by the LwM2M Server to access Object Instances and Resources available from a registered LwM2M Client. The interface provides this access through the use of "Create", "Read", "Read-Composite", "Write", "Write-Composite", "Delete", "Execute", "Write-Attributes", or "Discover" operations. The operations that a Resource supports are defined in the Object definition using the Object Template. The Object Template is described in Section [LwM2M Object Template and Guidelines (Normative)](). The Normative Objects defined by the LwM2M Enabler are described in Section [LwM2M Objects defined by OMA (Normative)]().

The LwM2M Client MUST ignore LwM2M Server operations on this interface until the registration procedure with the respective LwM2M Server is completed.

The LwM2M Client MUST reject any LwM2M Server operation on the Security Object (ID: 0) with a response code indicating that the operation is not authorized.

The LwM2M Client MUST reject any LwM2M Server operation on an OSCORE Object (ID: 21) with a response code indicating that the operation is not authorized.

The LwM2M Server SHOULD NOT perform any operation on this interface before replying to the registration of this LwM2M Client.

<figure class="text-center">
      <img src="images/example_flows_device_management.svg" alt="Example flows of Device Management & Service Enablement Interface">
      <figcaption>Example flows of Device Management & Service Enablement Interface</figcaption>
</figure>

The mapping to underlying transports is detailed in \[LwM2M-TRANSPORT\].

#### Read Operation

The "Read" operation is used to access the value of a Resource, a Resource Instance, an array of Resource Instances, an Object Instance or all the Object Instances of an Object. The "Read" operation has the following parameters:

<table>
    <caption>Read Parameters</caption>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>Required</th>
        <th>Default Value</th>
        <th>Notes</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>Object ID</td>
        <td>Yes</td>
        <td>-</td>
        <td>Indicates the Object.</td>
    </tr>
    <tr>
        <td>Object Instance ID</td>
        <td>No</td>
        <td>-</td>
        <td>Indicates the Object Instance to read.<br>
            If no Object Instance ID is indicated, then Resource ID and Resource Instance ID MUST NOT be indicated otherwise an error is returned by the Client; if no error, the authorized Instances of the Object are returned to the Server</td>
    </tr>
    <tr>
        <td>Resource ID</td>
        <td>No</td>
        <td>-</td>
        <td>Indicates the Resource to read. If the final target is not a Resource Instance (see below), then the Resource value is returned.
            If no Resource ID is indicated, then the Resource Instance ID MUST NOT be indicated as well, and the whole Object Instance is returned</td>
    </tr>
    <tr>
        <td>Resource Instance ID</td>
        <td>No</td>
        <td>-</td>
        <td>Indicates the Resource Instance to read. An error MUST be returned by the Client, if the Resource ID is absent or if the targeted Resource is not defined as a Multiple-Instance Resource.</td>
    </tr>
    </tbody>
</table>

If the Resource ID is specified and if the requested Resource does not support the "Read" operation, the LwM2M Client MUST return an error code indicating that the method is not allowed to the LwM2M Server.

If the Resource ID is not specified, the LwM2M Client MUST retrieve all the requested Resources except the Resource(s) which does not support the "Read" operation and sends the retrieved Resource(s) information to the LwM2M Server.

Any optional Resources included in the "Read" operation response that are not supported by, or unknown to, the LwM2M Server MUST NOT be interpreted as an error by the LwM2M Server.


#### Discover Operation

The "Discover" operation is used to discover LwM2M Attributes attached to an Object, Object Instances, and Resources. This operation can be used to discover which Resources are instantiated in a given Object Instance. The returned payload is a list of application/link-format CoRE Links \[RFC6690\] for each targeted Object, Object Instance, or Resource, along with their assigned or attached Attributes including the Object Version attribute if required (see Section [Object Versioning]() and [Table &lt;PROPERTIES&gt; Class Attributes]()).

The "Discover" operation has the following parameters:

<table>
    <caption>Discover Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Object Instance.</td>
        </tr>
        <tr>
            <td>Resource ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource.</td>
        </tr>
		<tr>
            <td>Depth</td>
            <td>No</td>
            <td>2 if only Object ID is specified.<br/>1 otherwise.</td>
            <td>Indicates the depth of the returned list of links relative to the targeted URI. Possible values are 0..3</td>
        </tr>
    </tbody>
</table>

The LwM2M Client SHOULD support the "Depth" parameter. If the LwM2M Client does not support the "Depth" parameter, it MUST ignore it and use the default value from [Table Depth Modifier]().

The LwM2M Client MUST respond to the "Discover" operation with the list of Object, Object Instances, Resources, and Resource Instances instantiated under the targeted Object according to [Table Depth Modifier]().

<table>
    <caption>Depth Modifier</caption>
    <thead>
        <tr>
            <th>Specified Parameters</th>
            <th>Depth 0</th>
            <th>Depth 1</th>
            <th>Depth 2</th>
            <th>Depth 3</th>
			<th>Default</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Object</td>
            <td>Object and Object Instances</td>
            <td>Object, Object Instances, and Resources</td>
            <td>Object, Object Instances, Resources, and Resource Instances</td>
            <td>Object, Object Instances, and Resources</td>
        </tr>
        <tr>
            <td>Object ID, Object Instance ID</td>
            <td>Object Instance</td>
            <td>Object Instance and Resources</td>
            <td>Object Instance, Resources, and Resource Instances</td>
            <td>Object Instance, Resources, and Resource Instances</td>
            <td>Object Instance and Resources</td>
        </tr>
        <tr>
            <td>Object ID, Object Instance ID, Resource ID</td>
            <td>Resource</td>
            <td>Resource and Resource Instances</td>
            <td>Resource and Resource Instances</td>
            <td>Resource and Resource Instances</td>
            <td>Resource and Resource Instances</td>
        </tr>
    </tbody>
</table>

In addition, the list of Attributes assigned to the Object, Object Instance, or Resource MUST be returned (see Section [Attributes Classification]()).

  For example:

 * when the "Discover" operation targets an Object with Object ID of 3, the response to the operation could be:

  &lt;/3&gt;;pmin=10, &lt;/3/0&gt;;pmax=60, &lt;/3/0/1&gt;, &lt;/3/0/2&gt;, &lt;/3/0/3&gt;, &lt;/3/0/4&gt;, &lt;/3/0/6&gt;;dim=2, &lt;/3/0/7&gt;;dim=2;gt=50;lt=42.2, &lt;/3/0/8&gt;;dim=2, &lt;/3/0/11&gt;, &lt;/3/0/16&gt;

  which means that the LwM2M Client supports the Device Object (Instance 0) Resources with IDs 1, 2, 3, 4, 6, 7, 8, 11, and 16 among the Resources of Device Info Object. A Maximum Period Attribute has been assigned to the Object and a Minimum Period Attribute has been assigned to the Object Instance.

 * when the "Discover" operation targets an Object with Object ID of 1 and a Depth of 1, the response to the operation could be:

  &lt;/1&gt;, &lt;/1/0&gt;, &lt;/1/4&gt;;pmax=300

  which means that the LwM2M Client has two Object Instances of the Server Object with IDs 0 and 4. A Maximum Period Attribute has been assigned to the Instance 4.

 * when the "Discover" operation targets an Object with Object ID of 3 and Object Instance ID of 0, the response to the operation could be:

  &lt;/3/0&gt;;pmin=10;pmax=60, &lt;/3/0/1&gt;, &lt;/3/0/2&gt;, &lt;/3/0/3&gt;, &lt;/3/0/4&gt;, &lt;/3/0/6&gt;;dim=2, &lt;/3/0/6/0&gt;, &lt;/3/0/6/3&gt;, &lt;/3/0/7&gt;;dim=2;gt=50;lt=42.2, &lt;/3/0/7/0&gt;, &lt;/3/0/7/1&gt;;lt=45, &lt;/3/0/8&gt;;dim=2, &lt;/3/0/8/1&gt;, &lt;/3/0/8/2&gt;, &lt;/3/0/11&gt;, &lt;/3/0/16&gt;

  which means that regarding the Device Object Instance, a Maximum Period Attribute has been assigned to this Instance level and a Minimum Period Attribute inherited from the Object level; the LwM2M Client supports the Multiple-Instance Resources 6, 7, and 8 with a dimension of 2 and has 2 additional Notification parameters assigned to Resource 7.

* when the "Discover" operation targets an Object with Object ID of 3, Object Instance ID of 0, and a Depth of 0, the response to the operation could be:

  &lt;/3/0&gt;;pmin=10;pmax=60

  which means that regarding the Device Object Instance, a Maximum Period Attribute has been assigned to this Instance level and a Minimum Period Attribute inherited from the Object level.

 * when the "Discover" operation targets an Object with Object ID of 3, Object Instance ID of 0, and Resource ID of 7 the response to the operation could be:

  &lt;/3/0/7&gt;;dim=2;pmin=10;pmax=60;gt=50;lt=42.2, &lt;/3/0/7/0&gt;, &lt;/3/0/7/1&gt;;lt=45

  which means that regarding the Power Source Voltage of the Device Object, two Resource Instances with IDs 0 and 1 are present; a Less Than Attribute has been assigned to this Resource, a Maximum Period Attribute and a Minimum Period Attribute are inherited from the Object and Object Instance levels; a different Less Than Attribute has been assigned to the Resource Instance 1.

* If a Resource, an Object Instance, or an Object have attributes for multiple LwM2M Servers, then the Attributes returned in the link, MUST only be related to the Server which performed the "Discover" operation. As example, for the Device Object (ID:3) having the Resource ID:7 with assigned Attributes from two Servers 1 and 2, then the answers to the "Discover" operation on both Servers will be differentiated e.g.

  from Server 1: Discover /3/0/7 could provide the answer: &lt;/3/0/7&gt;;dim=2;gt=50;lt=42.2, &lt;/3/0/7/0&gt;, &lt;/3/0/7/1&gt;

  from Server 2: Discover /3/0/7 could provide the answer: &lt;/3/0/7&gt;;dim=2;pmax=300;gt=80;lt=65.5, &lt;/3/0/7/0&gt;, &lt;/3/0/7/1&gt;

Any optional resources included in the "Discover" operation response that are not supported by, or unknown to, the LwM2M Server MUST NOT be interpreted as an error by the LwM2M Server.

#### Write Operation

The "Write" operation is used to change the value of a Resource, the value of a Resource Instance, the values of an array of Resources Instances or the values of multiple Resources from an Object Instance.
The "Write" operation can also be used to request the deletion or the allocation of specific Instances of a Multiple-Instance Resource.

The LwM2M Client MUST perform the operation only if all the Resources conveyed in the operation are allowed to support the "Write" operation. If any Resource does not support the "Write" operation, the LwM2M Client MUST inform the LwM2M Server that the Object Instance cannot perform the requested operation by returning an error code indicating that the method is not allowed.

The request includes the value to be written encoded in one of the data format defined in Section [Data Formats for Transferring Resource Information]().

The TLV, LwM2M CBOR, SenML CBOR or SenML JSON data format MUST be used in a "Write" request:
- when more than a single value of a Resource has to be changed 
- when one or several Instances of a Multiple-Instance Resource have to be deleted or allocated.

The Write request MUST be rejected:
- if the specified data format is not supported by the LwM2M Client
- or if, checking the value of the incoming Resource against its data type, at least one of the following conditions is not met:
   * the value matches the expected format
   * the value is in the range specified in the Object definition
   * if the value is an Objlnk value, it must either point to an Object actually present in the LwM2M Client (the value will then be ObjectID:MAX_ID), or point to an Object Instance actually present in the LwM2M Client, or contain the null pointer (the value will then be MAX_ID:MAX_ID)
- or if the deletion or allocation of an Instance of a Multiple-Instance Resource is not allowed by the LwM2M Client.

The LwM2M Client and LwM2M Server MUST support the following mechanisms to change multiple Resources or an array of Resource Instances:

* Replace: replaces the Object Instance or the Resource(s) with the new value provided in the "Write" operation.
           When the Resource is a Multiple-Instance Resource, the existing array of Resource Instances is replaced to the condition the LwM2M Client authorizes that operation.
* Partial Update: updates Resources provided in the new value and leaves other existing Resources unchanged.
                  When the Resource is a Multiple-Instance Resource, the existing array of Resource Instances is updated meaning some Instances may be created or overwritten to the condition the LwM2M Client authorizes such operations. Deleting via Partial Update is not possible.

Note: Partial Update can also be done by the "Write-Composite" operation.


The "Write" operation has the following parameters:

<table>
    <caption>Write Parameters</caption>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>Required</th>
        <th>Default Value</th>
        <th>Notes</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td> Object ID </td>
        <td> Yes </td>
        <td> - </td>
        <td> Indicates the Object. </td>
    </tr>
    <tr>
        <td> Object Instance ID </td>
        <td> Yes </td>
        <td> - </td>
        <td> Indicates the Object Instance to write. </td>
    </tr>
    <tr>
        <td> Resource ID </td>
        <td> No </td>
        <td> - </td>
        <td> Indicates the Resource to write. <br>If the final target is not a Resource Instance (see below), the payload is the new value for the Resource. The payload is the new value for the Resource. <br>
            If no Resource ID is indicated, the Resource Instance ID MUST NOT be indicated, then the value included payload is an Object Instance containing the Resource values.</td>
    </tr>
   <tr>
        <td> Resource Instance ID </td>
        <td> No </td>
        <td> - </td>
        <td> Indicates the Resource Instance to write. An error MUST be returned by the Client, if the Resource ID is absent, if the targeted Resource is not defined as a Multiple-Instance Resource, or if the targeted Resource Instance doesn't exist.
    </tr>
    <tr>
        <td> New Value </td>
        <td> Yes </td>
        <td> - </td>
        <td> The new value included in the payload to update the Object Instance, a Resource or a Resource Instance.</td>
    </tr>
    </tbody>
</table>
In a "Write" operation targeting an Object Instance, any optional Resources that are not supported by, or unknown to, the LwM2M Client MUST NOT be interpreted as an error by the LwM2M Client.

##### Examples

Let's consider a hypothetical Object 34 having a Multiple-Instance Resource 1 of type String with the following values:

```
/34/0/1/0: "Red"
/34/0/1/1: "Green"
```

The LwM2M Server performs a Write on /34/0/1 with the New Value containing:

```
[ { "n": "/34/0/1/1", "vs":"Yellow" },
  { "n": "/34/0/1/3", "vs":"Blue" }]
```

For a Write Replace, the Object new values will be:

```
/34/0/1/1: "Yellow"
/34/0/1/3: "Blue"
```

For a Write Partial Update, the Object new values will be:

```
/34/0/1/0: "Red"
/34/0/1/1: "Yellow"
/34/0/1/3: "Blue"
```

#### Write-Attributes Operation

Only Attributes from the &lt;NOTIFICATION&gt; class MAY be changed in using the "Write-Attributes" operation.

The general rules for Attributes which are specified in Section [Attributes Definitions and Rules]() fully apply here. [Table &lt;PROPERTIES&gt; Class Attributes]() in Section [Attributes Classification]() provides explanation on the Attributes supported by the "Write-Attributes" operation.

The operation permits multiple Attributes to be modified within the same operation.

{:page-break}

Including &lt;NOTIFICATION&gt; class Attributes specified in [Table &lt;PROPERTIES&gt; Class Attributes]() Section [Register Operation](), the "Write-Attributes" operation has the following parameters:

<table>
    <caption>Write-Attributes Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Object Instance. When this parameter is omitted, the Resource ID and Resource Instance ID parameters MUST NOT be indicated and Attributes in the parameters of the operation are valid for all resources of all instances of the Object according to the precedence rules (Section <a href="">Attributes Definitions and Rules</a>).</td>
        </tr>
        <tr>
            <td>Resource ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource. When this parameter is omitted, then the ResourceInstance ID MUST NOT be indicated as well and it means the Attributes of this operation are set at an upper level (Object or Object Instance level).</td>
        </tr>
        <tr>
            <td>Resource Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource Instance. The LwM2M Client MUST return an error if the Resource ID is absent or if the targeted Resource is not defined as a Multiple-Instance Resource.</td>
        </tr>
        <tr>
            <td>&lt;NOTIFICATION&gt; class Attributes</td>
            <td>Yes</td>
            <td></td>
            <td>Indicates which Attributes are concerned. When an Attribute is specified without value, it means this Attribute value is unset at the level specified in the operation (Object, Object Instance, Resource, or Resource Instance levels).</td>
        </tr>
    </tbody>
</table>


#### Execute Operation

The "Execute" operation is used by the LwM2M Server to initiate some action, and can only be performed on individual Resources. An LwM2M Client MUST return an error when the "Execute" operation is received for an Object Instance(s) or Resource Instance(s).

If the Resource does not support the "Execute" operation, the LwM2M Client MUST return an error code indicating that the method is not allowed to the LwM2M Server.

The "Execute" operation MAY have arguments.

<table>
    <caption>Execute parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object Instance.</td>
        </tr>
        <tr>
            <td>Resource ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Resource to execute.</td>
        </tr>
        <tr>
            <td>Arguments</td>
            <td>No</td>
            <td>-</td>
            <td>The "Execute" operation accepts arguments. Arguments MUST be in plain text following the ABNF syntax below.</td>
        </tr>
    </tbody>
</table>

The syntax of the arguments is as follows:

```
arglist = arg *( "," arg )
arg = DIGIT / DIGIT "=" "'" *CHAR "'"
DIGIT = "0" / "1" / "2" / "3" / "4" / "5" / "6" / "7" / "8" / "9"
CHAR = "!" / %x23-26 / %x28-5B / %x5D-7E
```

Examples of valid lists of arguments: 

* 5

* 2='10.3'

* 7, 0=' <https://www.omaspecworks.org>'

* 0,1,2,3,4

#### Create Operation

The "Create" operation is used by the LwM2M Server to create Object Instance(s) within the LwM2M Client. The "Create" operation MUST target an Object, and MUST follow the rules specified in Section [Access Control]() and its sub-sections. If any error occurs, it MUST NOT create anything.

The Object Instance created in the LwM2M Client by the LwM2M Server MUST be an Object type supported by the LwM2M Client and announced to the LwM2M Server using the "Register" and "Update" operations of the LwM2M Client Registration Interface.

Object Instance whose Object supports at most one Object Instance MUST be assigned an Object Instance ID of 0 when the Object Instance is Created.

The "Create" operation has the following parameters:

<table>
    <caption>Create parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object.</td>
        </tr>
        <tr>
            <td>New Value</td>
            <td>No</td>
            <td>-</td>
            <td>The new value included in the payload to create the Object Instance(s).</td>
        </tr>
    </tbody>
</table>

The new value included in the payload MUST follow the TLV, LwM2M CBOR, SenML CBOR or SenML JSON data format according to Section [Data Formats for Transferring Resource Information]().

When there is no reference to an Object Instance in the TLV/LwM2M CBOR payload of the "Create" operation, the LwM2M Client MUST assign the ID of the created Object Instance.

If a new Object Instance is created through that operation and the "Access Control-Enabled" configuration is used, then the LwM2M Client creates an Access Control Object Instance for the created Object Instance (see Section [Access Control]()) with the following requirements:

-   The Access Control Owner MUST be the LwM2M Server.
-   The LwM2M Server MUST have full access rights to the created Object Instance.

Any optional Resources included in the "Create" operation that are not supported by, or unknown to, the LwM2M Client MUST NOT be interpreted as an error by the LwM2M Client.

If New Value is not present or if it does not contain values for all Resources (mandatory and optional) of the Object, the LwM2M Client MAY populate the missing Resources with implementation dependent default values. If all the mandatory Resources of the created Object Instance are not instantiated, the LwM2M Client MUST return an error.

The values of the Read-only Resources MUST be setup by the LwM2M Client. If a value of a Read-only Resource is present in the "New Value" parameter then this value MUST NOT be processed nor should it result in an error. If the payload (New Value) conveys an Object Instance ID in conflict with one already present in the LwM2M Client then the entire request MUST be rejected and an error code indicating that the request is incorrect MUST be returned.

The LwM2M Client MAY reject the "Create" operation by returning an error code to the LwM2M Server.


#### Delete Operation

The "Delete" operation is used for LwM2M Server to delete an Object Instance or a Resource Instance within the LwM2M Client.

The Object Instance that is deleted in the LwM2M Client by the LwM2M Server MUST be an Object Instance that is announced by the LwM2M Client to the LwM2M Server using the "Register" and "Update" operations of the Client Registration Interface.

The only exception concerns the single Instance of the mandatory Device Object (ID:3) which SHALL NOT be affected by any Delete operation.

The LwM2M Client MAY reject the "Delete" operation by returning an error code to the LwM2M Server.

The Delete operation has the following parameters:

<table>
    <caption>Delete parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object Instance to delete if no Resource Instance ID is provided.</td>
        </tr>
        <tr>
            <td>Resource ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource. When this parameter is provided, Resource Instance ID parameters MUST be provided.</td>
        </tr>
        <tr>
            <td>Resource Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource Instance to delete.</td>
        </tr>
    </tbody>
</table>

#### Read-Composite Operation

The LwM2M Client MAY support the "Read-Composite" operation.

The "Read-Composite" operation can be used by the LwM2M Server to selectively read any combination of Objects, Object Instance(s), Resources, and/or Resource Instances of different or same Objects in a single request. The list of elements to be read are provided as SenML Pack where the records contain Base Name and/or Name Fields, but no Value fields as specified in \[RFC8790\]. The Read-Composite operation is treated as non-atomic and handled as best effort by the client. That is, if any of the requested resources do not have a valid value to return, they will not be included in the response. Section [SenML JSON]() shows examples of Read-Composite use.

The LwM2M Client MUST retrieve all the requested Resources except the Resource(s) which does not support the "Read" operation and sends the retrieved Resource(s) information to the LwM2M Server.

#### Write-Composite Operation

The LwM2M Client MAY support the "Write-Composite" operation.

In contrast to "Write" operation, the scope of which is limited to a Resource(s) of a single Instance of a single Object, the "Write-Composite" operation can be used by the Server to update values of a number of different Resources across different Instances of one or more Objects. Similar to Read-Composite the Write-Composite operation provides a list of all resources to be updated, and their new values, using one of LwM2M CBOR, SenML JSON/CBOR, or SenML-ETCH JSON/CBOR formats. Unlike for Write operation, the Resources that are not provided are not impacted by the operation. Examples are shown in Section [SenML JSON]().

The LwM2M Client MUST perform the operation only if all the Resources conveyed in the operation are allowed to support the "Write" operation. If any Resource does not support the "Write" operation, the LwM2M Client MUST inform the LwM2M Server that the Object Instance cannot perform the requested operation by returning an error code indicating that the method is not allowed.

The "Write-Composite" operation is atomic and cannot have partial success. That is, if the client supports this operation, it MUST reject a Server request where it cannot successfully write all the requested values to the requested list of Resources. Therefore, before processing Write-Composite, the client MUST ensure that all addressed objects exist and that the Server has write access to those Objects and Resources. 

### Information Reporting Interface

The Information Reporting Interface is used by an LwM2M Server to observe any changes in a Resource on a registered LwM2M Client, receiving notifications when new values are available. This observation relationship is initiated by sending an "Observe" or "Observe-Composite" operation to the L2M2M Client for an Object, an Object Instance or a Resource. An observation ends when a "Cancel Observation" or "Cancel Observation-Composite" operation is performed.

The LwM2M Server and the LwM2M Client MUST support all the operations on this interface unless clearly stated otherwise.

The LwM2M Client MUST ignore LwM2M Server operations on this interface until it received its Registration acknowledgement.

The LwM2M Server SHOULD NOT perform any operation on this interface before replying to the registration of this LwM2M Client.

The LwM2M Client MUST reject any LwM2M Server operation on the Security Object (ID: 0) with a response code indicating that the operation is not authorized.

The LwM2M Client MUST reject any LwM2M Server operation on an OSCORE Object (ID: 21) with a response code indicating that the operation is not authorized.

<figure class="text-center">
      <img src="images/example_information_reporting_interface.svg" alt="Example flow for Information Reporting Interface for the RSSI Resource of the Connectivity Monitoring Object of the example client ([Appendix LwM2M Objects defined by OMA (Normative)]())">
      <figcaption>Example flow for Information Reporting Interface for the RSSI Resource of the Connectivity Monitoring Object of the example client Appendix LwM2M Objects defined by OMA (Normative)</figcaption>
</figure>

The mapping to underlying transports is detailed in \[LwM2M-TRANSPORT\].

#### Observe Operation

The LwM2M Server initiates an observation request for changes of a specific Resource, Resources within an Object Instance or for all the Object Instances of an Object within the LwM2M Client.

Related attributes for "Observe" operation are described in [Table &lt;PROPERTIES&gt; Class Attributes]() in Section [Attributes Classification](). The general rules for Attributes which are specified in Section [Attributes Definitions and Rules]() fully apply here.

The "Observe" operation includes the following parameters:

<table>
    <caption>Observe Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Object ID</td>
            <td>Yes</td>
            <td>-</td>
            <td>Indicates the Object.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Object Instance to observe. If no Object Instance ID is indicated, then Resource ID and Resource Instance ID MUST NOT be indicated as well, otherwise an error is returned by the Client; if no error, all the Instances of the Object are observed.</td>
        </tr>
        <tr>
            <td>Resource ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource to observe. If no Resource ID is indicated, then the Resource Instance ID MUST NOT indicated as well, and the whole Object Instance is observed.</td>
        </tr>
        <tr>
            <td>Resource Instance ID</td>
            <td>No</td>
            <td>-</td>
            <td>Indicates the Resource Instance to observe. An error MUST be returned by the Client, if no Resource ID is indicated or if the targeted Resource is not defined as a Multiple-Instance Resource.</td>
        </tr>
        <tr>
            <td>Observation Attributes</td>
            <td>No</td>
            <td>-</td>
            <td>&lt;NOTIFICATION&gt; Class Attributes valid only for this Observation. When these attributes are present, all the attached or assigned attributes of the targeted URI MUST be ignored for this Observation.</td>
        </tr>
    </tbody>
</table>
If the Resource ID is specified and if the requested Resource does not support the "Read" operation, the LwM2M Client MUST return an error code indicating that the method is not allowed to the LwM2M Server.

If the Resource ID is not specified, the LwM2M Client MUST retrieve all the requested Resources except the Resource(s) which does not support the "Read" operation and sends the retrieved Resource(s) information to the LwM2M Server.

Until the LwM2M Client sends a new registration, the LwM2M Server expects the LwM2M Client to remember the observation requests. If an LwM2M Client forgets the observation requests (e.g. device factory reset) it MUST perform a new "Register" operation. The LwM2M Server MUST re-initiate the desired observation requests whenever the LwM2M Client registers.

In order to avoid network traffic increase, the LwM2M Client SHOULD maintain previous observation states in case of reboot, power cycle.

It has to be noted that an "Observe" operation containing only Object ID, will produce the report of all Object Instances information.

The LwM2M Client SHOULD support the "Observation Attributes" parameter. If the LwM2M Client does not support the "Observation Attributes" parameter, it MUST reject an observation that includes Observation Attributes. 

Note: The &lt;NOTIFICATION&gt; Class Attributes can also be configured by the "Write-Attributes" operation described in section [Write-Attributes Operation](). In that case, the Attributes will be permanent and apply to all Observations not specifying their own.

Note: The &lt;NOTIFICATION&gt; Class Attributes contained in the "Observation Attributes" parameter are not part of the LwM2M Client response to a Discover operation since they are neither attached nor assigned.

Note: When an LwM2M Client deregisters, the LwM2M Server should assume past states are nullified including the previous observations.

#### Notify Operation

The "Notify" operation is sent from the LwM2M Client to the LwM2M Server during a valid observation on an Object, Object Instance or Resource. The "Notify" operation MUST be sent when all conditions (i.e. Minimum Period, Maximum Period, Greater Than, Less Than, Step) are met. Those conditions are either "Observation Attributes" sent as parameters or attributes attached at the level of the "Observe" operation.

The LwM2M Client MUST retrieve all the observed Resources except the Resource(s) which does not support the "Read" operation and sends the retrieved Resource(s) information to the LwM2M Server.

Note: The conditions may be modified by the "Write-Attributes" operation after the observation request. The LwM2M Client behavior is implementation dependent for the evaluation of the Change Value Conditions started prior to the "Write-Attributes" operation. For deterministic behavior when changing observation attributes, the current observation SHOULD be cancelled and a new observation SHOULD be created with the desired observation attributes. However, some information may be lost in the transition between the two observations.

<table>
    <caption>Notify Parameters</caption>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Default Value</th>
            <th>Notes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Updated Value</td>
            <td>Yes</td>
            <td>-</td>
            <td>The new value included in the payload about the Object Instance or Resource.</td>
        </tr>
    </tbody>
</table>

The following example shows how the Minimum and Maximum period parameters work as shown in Section [Write-Attributes Operation](). An LwM2M Server makes an observation for a Temperature Resource that is updated inside the LwM2M Client at irregular periods (based on change). The LwM2M Server makes an observation when the Minimum Period = 10 Seconds and Maximum Period = 60 Seconds attributes have been set for that Resource. The LwM2M Client will wait at least 10 Seconds before sending a "Notify" operation to the LwM2M Server (even if the Resource has changed before that), and no longer than 60 Seconds before sending a "Notify" operation (even if the Resource has not changed yet). The "Notify" operation is sent anywhere between 10-60 seconds upon change.

Note: In case an "Observe" operation is initiated on a Resource, an Object Instance or an Object without any conditions previously configured, and with the "Default Minimum Period" in the LwM2M Server Object set to 0 (possibly by default), the "Notify" operation will be sent upon any change of, respectively, the observed Resource value, any Resource value of the observed Object Instance or any Resource value of any Instance of the observed Object. As specified in Section [Observe Operation]() and in [Table Observe Parameters](), in case of an "Observe" operation on a certain Object the "Notify" operation includes all Resources of all Instances of the observed Object.

<figure class="text-center">
      <img src="images/example_minimum_maximum_periods.svg" alt="Example of Minimum and Maximum periods in an Observation">
      <figcaption>Example of Minimum and Maximum periods in an Observation</figcaption>
</figure>

In this example the Minimum Period has been set to 10 and the Maximum Period set to 60 for the Resource /4/0/2 before making the observation.

#### Cancel Observation Operation

The "Cancel Observation" operation is sent from the LwM2M Server to the LwM2M Client to end an observation relationship that was previously created with an "Observe" operation.

#### Observe-Composite Operation

The LwM2M Client MAY support the "Observe-Composite" operation.

The LwM2M Server can use the "Observe-Composite" operation to initiate observations for a group of resources and/or resource instances across multiple object instances within the client. As with the "Read-Composite" operation, the list of elements to be observed is provided as a separate parameter to the operation in SenML JSON/CBOR format.

The &lt;NOTIFICATION&gt; Class Attributes for each resource that is observed through the "Observe-Composite" operation may be individually configured by the LwM2M server using the "Write-Attribute". Each resource can have multiple observe conditions attached. If any of the conditions attached to one or more resources under observation meets the notification criteria a notify will be generated by the LwM2M client, which will include the value for each of the resources listed in the "Observe-Composite" operation. Hence, the resources that have not met the notify condition will still be included in the notification message.

Note: It is the responsibility of the LwM2M Server to ensure that the Minimum and Maximum Period Attributes attached to observed resources follow the rules defined in Section [Attributes Classification](). For example, the Minimum Period Attributes attached to targeted resources must be less than the Maximum Period Attributes attached to all targeted resources. 

As with the "Observe" operation, \<NOTIFICATION\> Class Attributes can be provided as a separate parameter to the operation. However, these attributes MUST have the Object Assignation Level, i.e. Minimum Period, Maximum Period, Minimum Evaluation Period, Maximum Evaluation Period, and Confirmable Notification. When these attributes are present, all the attached or assigned attributes with the Object Assignation Level of the targeted URI MUST be ignored for this Observation-Composite.

For example, the following attributes are attached to the Device Object and the Connectivity Monitoring Object:

```
</3>;pmin=60
</4>;pmax=300
```

if the LwM2M Server performs an Observe-Composite operation on the Resources /3/0/8 and /4/0/2 with a parameter Minimum Evaluation Period set to 30, when evaluating the Notification conditions for this Observation-Composite, the LwM2M Client will ignore the Minimum Period and Maximum Period attributes inherited by the Resources and will consider only the Minimum Evaluation Period on both Resources.

#### Cancel Observation-Composite Operation

If the "Observe-Composite" operation is supported by the client, the "Cancel Observation-Composite" operation MUST be supported by the Client.

The "Cancel Observation-Composite" operation is sent from the LwM2M Server to the LwM2M Client to end the previously set up composite observation relationship.

#### Send Operation

The LwM2M Client and the LwM2M Server MAY support the "Send" operation.

The "Send" operation is used by the LwM2M Client to send data to the LwM2M Server without explicit request by that LwM2M Server.

The "Send" operation can be used by the LwM2M Client to report values for Resources and Resource Instances of LwM2M Object Instance(s) to the LwM2M Server. The Resources and Resource Instances to send is implementation specific. The LwM2M Server MAY use the "Mute Send" Resource in the LwM2M Server Object (Resource ID 23) to enable or disable the use of the "Send" operation. When information reporting should be controlled by the LwM2M Server, the "Observe" or "Observe-Composite" operations can be used.

The reported LwM2M Object Instances (potentially different Object types) MUST have been registered by the LwM2M Client to the LwM2M Server. That LwM2M Server MUST have Read access right granted on the Object Instances of the reportable Resources which MUST support the Read operation (see Section [Authorization]()). If these criteria are not met for some Resources, the LwM2M Client MUST NOT include those Resources in the "Send" operation.

Any optional Resources included in the "Send" operation that are not supported by, or unknown to, the LwM2M Server MUST NOT be interpreted as an error by the LwM2M Server.

In addition, if any of the rules mentioned below is violated, the Server MUST respond with an error in reply to the "Send" operation. 

The value included in the payload MUST be either LwM2M CBOR, SenML JSON, or SenML CBOR format described in Section [Data Formats for Transferring Resource Information]().
As example:

Reporting the location of the LwM2M Client and the radio signal strength in a JSON payload:
```
Send
New Value:
[
  {"n":"/6/0/0", "v":43.61092},
  {"n":"/6/0/1", "v":3.87723},
  {"n":"/4/0/2", "v":-49}
]
```

## Identifiers and Resources

This section defines the identifiers and resource model for the LwM2M Enabler.

### Resource Model

The LwM2M Enabler defines a simple resource model where each piece of information made available by the LwM2M Client is a Resource. Resources are logically organized into Objects. Each Resource is given a unique identifier within that Object and a data type among those defined in Section [Data Types (Normative)]().

[Figure Relationship between LwM2M Client, Object, and Resources]() illustrates this structure, and the relationship between Resources, Objects, and the LwM2M Client. The LwM2M Client may have any number of Resources, each of which belongs to an Object; for example the Firmware Update Object contains all the Resources used for firmware update purposes.

<figure class="text-center">
      <img src="images/relationship_client_object_resources.svg" alt="Relationship between LwM2M Client, Object, and Resources">
      <figcaption>Relationship between LwM2M Client, Object, and Resources</figcaption>
</figure>

Each Object, defined for the LwM2M Enabler, is assigned a unique OMA LwM2M Object identifier allocated and maintained by \[OMNA\]. The LwM2M Enabler defines standard Objects and Resources, see Section [LwM2M Objects defined by OMA (Normative)](). Further Objects may be added by OMA or other organizations to enable additional M2M Services.

As an Object only specifies a grouping of Resources, an Object MUST first be instantiated so that the LwM2M Client can use the Resources of such an Object and the associated functionalities.

When an Object is instantiated – either by the LwM2M Server or the LwM2M Client – an Object Instance is created with a subset of the Resources defined in the Object specification; an LwM2M Server can then access that Object Instance and its set of instantiated Resources.

A Resource which is instantiated within an Object Instance is a Resource which can either:

-   contain a value (if the Resource is Readable and/or Writeable)

-   or can be addressed by an LwM2M Server to trigger an action in the LwM2M Client (if the Resource is Executable)

Data Type checking on a Resource value MUST be performed:
- by the Client when the Server tries to set such a Resource,
- by the Server when the Server retrieves such a Resource

The Client MUST reject a request, if an error is detected when checking an incoming Resource value against its data type.

The Object specification defines the operations (Read, Write, Execute) which are individually supported by the Resources belonging to that Object; this specification also defines the Mandatory or Optional characteristics of such Resources.

A Resource specified as Mandatory within an Object MUST be instantiated in any Instance of that Object.

A Resource specified as Optional within an Object MAY be omitted from some or even all Instances of that Object.

As illustration, the following example using the discover operation on the Server Object, exposes a configuration in which the Server Object (ID:1) has 2 Instances (ID:0, ID:1): the Optional Resources ID:2, ID:4 are only instantiated in the Instance 1 of the Object, while the Optional Resources ID:3 and ID:5 are not instantiated in either of the Server Object Instances. In Server Object ID:1, the Resources 0,1, and 6,7,8 are Mandatory Resources.

According to the DISCOVER /1 request, the following payload is returned:

&lt;/1/0/0&gt;,&lt;/1/0/1&gt;,&lt;/1/0/6&gt;,&lt;/1/0/7&gt;, &lt;/1/0/8&gt;, &lt;/1/1/0&gt;,&lt;/1/1/1&gt;,&lt;/1/1/2&gt;,&lt;/1/1/4&gt;,&lt;/1/1/6&gt;,&lt;/1/1/7&gt;, &lt;/1/1/8&gt;

Objects and Resources have the capability to have multiple instances. Multiple-Instance Resources can be instantiated by LwM2M Server operations in using SenML JSON, SenML CBOR, LwM2M CBOR, or TLV formats (see Section [Data Formats for Transferring Resource Information]()). The LwM2M Client also has the capability to instantiate Single or Multiple-Instance Resources.

The LwM2M Server performs operations on an Object, Object Instance and Resources as described in Section [Interfaces](). These operations are conveyed as described in \[LwM2M-TRANSPORT\] and how to convey the Operation data is defined in Section [Data Formats for Transferring Resource Information]().

The LwM2M Enabler defines an access control mechanism per Object Instance. Object Instances SHOULD have an associated Access Control Object Instance. An Access Control Object Instance contains Access Control Lists (ACLs) that define which operations on a given Object Instance are allowed for which LwM2M Server(s).

[Figure Example of Supported operations and Associated Access Control Object Instance]() shows an example of the operations the Resources support and how Object Instances and Resources are associated with Access Control Object Instance. In the example, Object Instance 0 for Object 1 has 2 Resources. Resource 1 supports the "Read", "Write" operations, while Resource 0 supports only the "Read" operation. The associated Access Control Object Instance has ACL of Object Instance 0 for Object 1. Server1 is authorized to perform "Read" and "Write" operations to the Object Instance 0 for Object 1 and Resources of the Object Instance. However, due to the supported operations of each Resource, Server1 can perform the "Read" operation on Resource 1 and 0, and also can perform the "Write" operations on Resource 1, but Server1 cannot perform the "Write" operation on Resource 0. The detailed access control mechanism is defined in Section [Access Control]().

<figure class="text-center">
      <img src="images/example_supported_operations.svg" alt="Example of Supported operations and Associated Access Control Object Instance">
      <figcaption>Example of Supported operations and Associated Access Control Object Instance</figcaption>
</figure>

### Object Versioning

#### General Policy

The official specification of the Objects is available at \[OMNA\].

An LwM2M Server MUST be able to determine without ambiguity the specification of the Objects intended to be registered by the LwM2M Client. 

An LwM2M Object can evolve. Object versioning aims at identifying these LwM2M Object modifications, which can be categorized in two types:

-   Evolution of type I: representing non-backwards-compatible ("breaking") evolutions are:
    -   changing the "Instances" characteristic of the Object.
    -   changing the normative text in the Object description.
    -   adding or removing a mandatory Resource.
    -   modifying the list of allowed operations of a Resource.
    -   changing the "Instances" characteristic of a Resource.
    -   changing the Data Type of a Resource.
    -   modifying the Range of a Resource value (not associated with new enumeration values described in type II).
    -   removing a Resource enumeration value.
    -   changing the unit of a Resource.
    -   changing the normative text in a Resource description.

-   Evolution of type II: representing backwards-compatible ("non-breaking") evolutions are:
    -   changing the non-normative text in the Object description.
    -   adding or removing an optional Resource.
    -   adding a Resource enumeration value.
    -   reusing a Resource enumeration value, which was marked as "reserved".
    -   changing the non-normative text in a Resource description.

Any other changes are forbidden (e.g. changing the name of an Object, changing the name of a Resource, or reusing a previously removed Resource ID).

With Object versioning, the Object Identifier is not changed but a new URN identifying that particular version of the Object specification MUST be registered according to the following format

   "urn:oma:lwm2m:{oma, ext, x}:ObjectID\[:{version}\]" where 'version' is the Object Version as defined in the following section

#### Object Version format

The Object Version of an Object is composed of 2 digits separated by a dot '.':

-   the first digit represents the Major Version of the Object: this digit marks the non-backward compatible evolution of such an Object (Object evolution of type I: Section [General Policy]())

-   the second digit represents the Minor Version of the Object: this digit marks the backward compatible evolution of such an Object (Object evolution of type II: Section [General Policy]())

By convention when an Object is in version 1.0, the Object Version MAY be omitted in the URN.

To be more precise, two separate URNs are accepted as valid for the corresponding version of the object specification:

-   the URN where the Object Version is mentioned explicitly: "urn:oma:lwm2m:{oma, ext, x}:ObjectID:1.0"

-   the URN where the Object Version is absent: "urn:oma:lwm2m:{oma, ext, x}:ObjectID" (and supposed to be 1.0).

Example: "urn:oma:lwm2m:oma:44:2.2"

This URN uniquely identifies Object ID:44 in its version "2.2". Registered Objects are available at \[OMNA\], see Section [Identifiers]() and Section [LwM2M Schema and Object Definition File (Informative)]() for further information.

#### Object Definition and Object Version Usage

Objects can be either:

* Core Objects, which are LwM2M Objects specified within the LwM2M Enabler specification (e.g. the Device Object).
* Non-core Objects, which are LwM2M Objects specified outside of an LwM2M Enabler specification (e.g. the Cellular Connectivity Object, which is defined in its own OMA specification, or any Object from a third party).

An LwM2M Client can always attach Object Version information to an Object. In certain circumstances Object Version information can, however, be omitted.  

If a Core Object version does not correspond to version contained in the LwM2M Enabler release supported by the LwM2M Client, the Object Version MUST be provided by the LwM2M Client to the LwM2M Server.

If a Non-core Object is not version 1.0, the Object Version MUST be provided by the LwM2M Client to the LwM2M Server.

In "Register" and "Discover" operations, when the Object Version of a given Object is communicated, the LwM2M Client MUST use the "ver" (object version) &lt;PROPERTIES&gt; Class attribute associated to that Object.

A few examples:

1. An LwM2M Client supporting LwM2M Enabler version 1.1 registers the Server Object version 1.1 ("urn:oma:lwm2m:oma:1:1.1"), and the Device Object version 1.1 ("urn:oma:lwm2m:oma:3:1.1"). The registration payload is: 

   &lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/3/0&gt;

2. An LwM2M Client supporting LwM2M Enabler version 1.1 registers the Server Object version 1.0 ("urn:oma:lwm2m:oma:1"), and the Device Object version 1.1 ("urn:oma:lwm2m:oma:3:1.1"). The registration payload is: 

   &lt;/1&gt;;ver=1.0,&lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/3/0&gt;

3. At \[OMNA\], the Object ID:44 will be registered at least twice:

   - with the URN "urn:oma:lwm2m:oma:44" (version 1.0)
   - with the URN "urn:oma:lwm2m:oma:44:2.2"

   An LwM2M Client supporting LwM2M Enabler version 1.0 registers this Object in version 2.2 along with the Server Object version 1.0 ("urn:oma:lwm2m:oma:1"), and the Device Object version 1.0 ("urn:oma:lwm2m:oma:3"). The registration payload is: 

   &lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/3/0&gt;,&lt;/44/0&gt;;ver=2.2

4. An LwM2M Client supporting LwM2M Enabler version 1.1 registers the Server Object version 1.1 ("urn:oma:lwm2m:oma:1.1"), the Device Object version 1.1 ("urn:oma:lwm2m:oma:3:1.1"), and the Connectivity Monitoring Object version 1.2 ("urn:oma:lwm2m:oma:4:1.2"). Because each of these Object versions correspond to the Object versions released as part of the LwM2M Enabler version 1.1, the Object version information can be omitted. The registration payload is: 

   &lt;/1&gt;,&lt;/1/0&gt;,&lt;/1/1&gt;,&lt;/3/0&gt;,&lt;/4/0&gt;

### Identifiers

The LwM2M Enabler defines specific identifiers for entities used within the LwM2M Protocol. These identifiers are defined in [Table LwM2M Identifiers]().

{:page-break}

<table>
    <caption>LwM2M Identifiers</caption>
    <thead>
        <tr>
            <th>Identifier</th>
            <th>Format</th>
            <th>Description</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>Endpoint Client Name</td>
            <td>String</td>
            <td><p>Identifies the LwM2M Client on one LwM2M Server (including LwM2M Bootstrap-Server). </p>
                <p>This parameter is optional and provided to the LwM2M Server during Registration, also provided to LwM2M Bootstrap-Server when executing the Bootstrap procedure. It MUST be provided when the security protocol does not provide an authenticated identifier or this information is not available for the server.</p>
                <p>The Endpoint Client Name is a string. Recommended URI and URN formats are documented in <a href="">Endpoint Client Name</a>.</p></td>
        </tr>
        <tr>
            <td>LwM2M Bootstrap-Server URI</td>
            <td>URI</td>
            <td>Uniquely identifies the LwM2M Bootstrap-Server. Provided to the LwM2M Client during the Bootstrap procedure.</td>
        </tr>
        <tr>
            <td>LwM2M Server URI</td>
            <td>URI</td>
            <td>Uniquely identifies the LwM2M Server. Provided to the Client during Bootstrap procedure.</td>
        </tr>
        <tr>
            <td>Short Server ID</td>
            <td>16-bit unsigned integer</td>
            <td><p>Uniquely identifies each LwM2M Server configured for the LwM2M Client. Assigned during the Bootstrap procedure.</p>
                <p>The values '0' and MAX_ID '65535' are reserved values and MUST NOT be used for identifying an LwM2M Server.</p></td>
        </tr>
        <tr>
            <td>Human Readable Object URN</td>
            <td>URN for the OMA Management Object</td>
            <td>Assigned by the Object specification.</td>
        </tr>
        <tr>
            <td>Object ID</td>
            <td>16-bit unsigned integer</td>
            <td>Uniquely identifies an Object in the LwM2M Client. This identifier is assigned by OMA.<br>
                MAX_ID 65535 is a reserved value and MUST NOT be used for identifying an Object.</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>16-bit unsigned integer</td>
            <td>Uniquely identifies an Object Instance of an Object within the LwM2M Client. This identifier is assigned by the LwM2M Client or LwM2M Server.<br>
                MAX_ID 65535 is a reserved value and MUST NOT be used for identifying an Object Instance.</td>
        </tr>
        <tr>
            <td>Resource ID</td>
            <td>16-bit unsigned integer</td>
            <td>Uniquely identifies a Resource within an Object. Short integer ID, with a range assigned by the Object specification and unique to that Object, and a Reusable Resource ID range assigned by OMA and re-usable between Objects.<br>
                MAX_ID 65535 is a reserved value and MUST NOT be used for identifying a Resource.</td>
        </tr>
        <tr>
            <td>Resource Instance ID</td>
            <td>16-bit unsigned integer</td>
            <td>Uniquely identifies a Resource Instance of a Resource. This identifier is assigned by an LwM2M Client or LwM2M Server.<br>
                MAX_ID 65535 is a reserved value and MUST NOT be used for identifying a Resource Instance.</td>
        </tr>
    </tbody>
</table>

#### Endpoint Client Name

The Endpoint Client Name is a string. URIs and URNs are RECOMMENDED formats for this identifier. The Endpoint Client Name identifier MUST be unique at the server or servers it is being used with. Note that the Endpoint Client Name is unauthenticated and can be set to arbitrary value by a misconfigured or malicious client and hence MUST NOT be used alone for any decision making without prior matching the Endpoint Client Name against the identifier used with the security protocol protecting LwM2M communication. This parameter MAY be omitted when the security protocol provides to the server an authenticated identifier that is identical to this parameter. For more discussion consult the security consideration section in the \[LwM2M-TRANSPORT\] specification. This security consideration section also provides a description of the privacy implications of re-using the same identifiers across multiple servers. 

This specification RECOMMENDS the Endpoint Client Name to be in a URI or a URN format for uniqueness reasons. The following table lists recommended formats. Other URI and URN formats MAY also be used. In particular, URN formats defined in \[DMREPPRO\] Section [Information Reporting Interface]() can be used.
Note: Implementations need to be careful when using the Endpoint Client Name to perform database lookups due to the risk of SQL injection attacks. 

{:page-break}

<table>
    <caption>Endpoint Client Name</caption>
    <thead>
        <tr>
            <th>
                Format
            </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><p>UUID URN: Identify a device using a Universally Unique IDentifier (UUID). The UUID specifies a valid, hex digit character string as defined in [RFC4122]. The format of the URN is<br />
                urn:uuid:########-####-####-####-############</p>
                <p>OPS URN: Identify a device using the format &lt;OUI&gt; &quot;-&quot; &lt;ProductClass&gt; &quot;-&quot; &lt;SerialNumber&gt; as defined in Section 3.4.4 of [TR-069]. The format of the URN is urn:dev:ops:&lt;OUI&gt; &quot;-&quot; &lt;ProductClass&gt; &quot;-&quot; &lt;SerialNumber&gt;.</p>
                <p>OS URN: Identify a device using the format &lt;OUI&gt; &quot;-&quot;&lt;SerialNumber&gt; as defined in Section 3.4.4 of [TR-069]. The format of the URN is urn:dev:os:&lt;OUI&gt; &quot;-&quot;&lt;SerialNumber&gt;.</p>
                <p>IMEI URN: Identify a device using an International Mobile Equipment Identifiers [3GPP 23.003]. The IMEI URN specifies a valid, 15 digit IMEI. The format of the URN is urn:imei:###############</p>
                <p>ESN URN: Identify a device using an Electronic Serial Number. The ESN specifies a valid, 8 digit ESN. The format of the URN is urn:esn:########</p>
                <p>MEID URN: Identify a device using a Mobile Equipment Identifier. The MEID URN specifies a valid, 14 digit MEID. The format of the URN is urn:meid:##############</p>
                <p>IMEI-MSISDN URN: Identify a device using a combination of International Mobile Equipment Identifier [3GPP 23.003] and MSISDN. IMEI is 15 digits and MSISDN is 15 digits. The format of the URN is urn:imei-msisdn: ###############-###############</p>
                <p>IMEI-IMSI URN: Identify a device using a combination of International Mobile Equipment Identifier [3GPP 23.003] and IMSI. IMEI is 15 digits and IMSI is 15 digits. The format of the URN is urn:imei-imsi: ###############-###############</p>
                <p>NAI URN: Identify a device using a combination of "Local Identifier@Domain Identifier" [3GPP 23.003]. Further [3GPP 23.003] references RFC 4282, which is replaced by [RFC7542] provides total limit to 63 octets (though allowed length is 253 octets which is not advised in [RFC7542] as it may hinder different systems to accommodate that many octets). The format of the URN Is urn:extid:###############################################################. 63 octets. <br> 
                  Examples are:  <br>
                    <ol type="1">
                    <li>The NAI 123456789@domain.com is represented as urn:nai:123456789@domain.com</li>
                    <li>The NAI user@homerealm.example.net is represented as urn:nai:user@homerealm.example.net</li>
                    </ol>    
            </td>
        </tr>
    </tbody>
</table>

If a URN identifier from the above table is used, it MUST adhere to the specified format.

Other URN formats MAY be used. In particular, URN formats defined in Section 5.5 of \[DMREPPRO\] can be used.

#### Reusable Resources

When Objects are designed for a similar purpose, for example Objects for use in network management, or Objects for use in embedded device automation, similar Resources are useful in more than one Object. For example in embedded device automation, Objects for different purposes may contain common Resource types such as digital input, digital output, analogue input, analogue output, dimmer value, unit, min measurement, max measurement, value range etc.

If a Resource can feasibly be re-used with the same meaning in multiple Object definitions, it can be defined as a Reusable Resource ID and registered with \[OMNA\]. Other Objects may then make use of this Reusable Resource ID in another Object definition.

The definition of a Reusable Resource and its usage when hosted in an Object specification MUST follow several rules:

-   the Name, ID, Operation, Type, Range and Units are frozen characteristics when the Reusable Resource is registered at \[OMNA\] and cannot not be changed when such a Resource is specified in the definition of a hosting Object.

-   the registered Description field of a Reusable Resource is also a frozen characteristic; when extension is required to fit the real need of the Object hosting such a Resource, that extension must be mentioned in the Object specification but outside of the Description field itself; furthermore any extension MUST be compatible with the content of the registered Description field.

-   a Reusable Resource is registered without defining "Multiple-Resource", or "Mandatory" characteristics; both characteristics will be determined when such a Resource is specified in the definition of a hosting Object.

Note: The strict guidelines about Reusable Resources, as indicated in the above bullets, are specified to ensure that the definition remains consistent across different implementations. \[OMNA\] is the only official reference for Reusable Resources to which all implementations should adhere. There is no versioning for a resource definition. Name, ID, Operation, Type, Range, and Units of the Reusable Resource cannot change. In addition, any semantics captured in the Description cannot change. If the existing Reusable Resources need to evolve or are not sufficient, it is recommended to propose a new Reusable Resource.

### Data Formats for Transferring Resource Information

The following data formats are defined by the LwM2M Enabler in this section: plain text, opaque, TLV, LwM2M TS 1.0 JSON, CBOR, LwM2M CBOR, SenML JSON, and SenML CBOR. Additionally, the LwM2M Enabler uses the CoRE Link data format defined in \[RFC6690\].

The LwM2M Server MUST support all data formats, including TLV that was mandatory to support for LwM2M TS 1.0 Clients.

The LwM2M Client MUST support plain text, opaque, and CoRE Link data formats and it SHOULD support at least one of SenML CBOR, SenML JSON, or LwM2M CBOR data formats. In addition, an LwM2M Client MAY choose to support other data formats. LwM2M Clients supporting LwM2M TS 1.1 or newer SHOULD NOT use the legacy TLV or JSON formats.

Messages containing data MUST specify the payload encoding by using one of the supported data formats.

An LwM2M Server data request MAY contain an option specifying the data formats the Server would prefer to receive for the payload; if this data format is not accepted by the LwM2M Client, the request is rejected; if the LwM2M Client doesn't support that option or if the LwM2M Server expresses no data format preference, the LwM2M Client will use its own preferred data format.

The IANA registered Media Types supported in \[LwM2M-TS\_1.0\] are listed in the table below.

<table>
    <caption>IANA registered Media Types supported in LwM2M TS 1.0</caption>
    <thead>
        <tr>
            <th>Data Format</th>
            <th>IANA Media Type</th>
            <th>Numeric Content-Formats [CoAP]</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Plain Text</td>
            <td>text/plain</td>
            <td>0</td>
        </tr>
        <tr>
            <td>CoRE Link Format</td>
            <td>application/link-format</td>
            <td>40</td>
        </tr>
        <tr>
            <td>Opaque</td>
            <td>application/octet-stream</td>
            <td>42</td>
        </tr>
        <tr>
            <td>TLV</td>
            <td>application/vnd.oma.lwm2m+tlv</td>
            <td>11542</td>
        </tr>
        <tr>
            <td>JSON</td>
            <td>application/vnd.oma.lwm2m+json</td>
            <td>11543</td>
        </tr>
    </tbody>
</table>

In addition, \[LwM2M-TS\_1.1\] adds support for the following standardized media types.

<table>
    <caption>Additional standardized Media Types supported in LwM2M TS 1.1</caption>
    <thead>
        <tr>
            <th>Data Format</th>
            <th>IANA Media Type</th>
            <th>Numeric Content-Formats [CoAP]</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>CBOR</td>
            <td>application/cbor</td>
            <td>60</td>
        </tr>
        <tr>
            <td>SenML JSON</td>
            <td>application/senml+json</td>
            <td>110</td>
        </tr>
        <tr>
            <td>SenML CBOR</td>
            <td>application/senml+cbor</td>
            <td>112</td>
        </tr>
    </tbody>
</table>

{:page-break}

In addition, this specification adds support for the following IANA registered Media Type.

<table>
    <caption>Additional IANA registered Media Type supported in LwM2M TS 1.2</caption>
    <thead>
        <tr>
            <th>Data Format</th>
            <th>IANA Media Type</th>
            <th>Numeric Content-Formats [CoAP]</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>LwM2M CBOR</td>
            <td>application/vnd.oma.lwm2m+cbor</td>
            <td>TBD</td>
        </tr>
	<tr>
            <td>SenML-ETCH JSON</td>
            <td>application/senml-etch+json</td>
            <td>320</td>
        </tr>
	<tr>
            <td>SenML-ETCH CBOR</td>
            <td>application/senml-etch+cbor</td>
            <td>322</td>
        </tr>
    </tbody>
</table>

#### Plain Text

The plain text format is used for "Read" and "Write" operations on singular Resources or Resource Instances where the value of the Resource is represented as described in Section [Data Types (Normative)]().

For example, a request to the example client's Device Object Instance, Manufacturer Resource would return the following plain text payload:

<table>
 <tr>
  <td>
   Req: Get /3/0/0 <br><br> Res: 2.05 Content <br> Open Mobile Alliance
  </td>
 </tr>
 </table>

This data format has a Media Type of text/plain.

#### Opaque

The opaque format is used for "Read" and "Write" operations on singular Resources or Resource Instances where the value of the Resource is an opaque sequence of binary octets. This data format is used for binary Resources such as firmware images or application specific binary formats.

This data format has a Media Type of application/octet-stream.

#### CBOR

The Concise Binary Object Representation format is used for "Read" and "Write" operations on singular Resources or Resource Instances.

This data format has a Media Type of application/cbor which covers all the LwM2M data types via the use of its major types with or without optional tags.

#### LwM2M CBOR

When an LwM2M Client is supporting the LwM2M CBOR data format and the format is used to transport resource values for LwM2M operations, LwM2M CBOR payload MUST use the format defined in this section.

This data format has a Media Type of application/vnd.oma.lwm2m+cbor.

The syntax of this data format is as follows:

```abnf
payload = CBOR_map_with_length 1*(ID, VALUE) / CBOR_infinite_map_start 1*(ID, VALUE) CBOR_break
ID = CBOR_unsigned_integer / CBOR_array_with_length 1*(CBOR_unsigned_integer) / CBOR_infinite_array_start 1*(CBOR_unsigned_integer) CBOR_break
VALUE = CBOR_value / payload
```

According to the ABNF syntax above, the values are encoded in a CBOR map (Major type 5). The key of the data items is the ID of the underlying Object, Object Instance, Resource, or Resource Instance. Except when used for a Write or Create operation, the IDs inside the top-level payload MUST start with the Object ID.

##### Single Resource Example

A request to the Device Object on Resource 0 of the LwM2M example client from Appendix F (Read /3/0/0) would return the following LwM2M CBOR payload. This example has a size of 26 bytes.

```
A1                                             # map(1)
   83                                          # array(3)
      03                                       # unsigned(3)
      00                                       # unsigned(0)
      00                                       # unsigned(0)
   74                                          # text(20)
      4F70656E204D6F62696C6520416C6C69616E6365 # "Open Mobile Alliance"
```

The same example using the CBOR diagnostic notation is shown below.

```
{[3, 0, 0]: "Open Mobile Alliance"}
```

Note that the following payload is also valid:

```
A1                                      # map(1)
   03                                   # unsigned(3)
   A1                                   # map(1)
      00                                # unsigned(0)
      A1                                # map(1)
         00                             # unsigned(0)
         74                             # text(20)
            4F70656E204D6F62696C6520416C6C69616E6365 # "Open Mobile Alliance"
```

```
{3: {0: {0: "Open Mobile Alliance"}}}
```

##### Multiple Resource Example

A request to the Device Object on Resource 6 of the LwM2M example client from Appendix F (Read /3/0/6) would return the following LwM2M CBOR payload. This example has a size of 10 bytes.

```
A1       # map(1)
   83    # array(3)
      03 # unsigned(3)
      00 # unsigned(0)
      06 # unsigned(6)
   A2    # map(2)
      00 # unsigned(0)
      01 # unsigned(1)
      01 # unsigned(1)
      05 # unsigned(5)
```

The same example using the CBOR diagnostic notation is shown below.

```
{[3, 0, 6]: {0: 1,
             1: 5}}
```

##### Single Object Instance Example

A request to the Device Object (Read /3/0) of the LwM2M example client would return the following LwM2M CBOR payload. This example has a size of 118 bytes.

{:page-break}

```
A1                                      # map(1)
   82                                   # array(2)
      03                                # unsigned(3)
      00                                # unsigned(0)
   AD                                   # map(13)
      00                                # unsigned(0)
      74                                # text(20)
         4F70656E204D6F62696C6520416C6C69616E6365 # "Open Mobile Alliance"
      01                                # unsigned(1)
      76                                # text(22)
         4C69676874776569676874204D324D20436C69656E74 # "Lightweight M2M Client"
      02                                # unsigned(2)
      69                                # text(9)
         333435303030313233             # "345000123"
      03                                # unsigned(3)
      63                                # text(3)
         312E30                         # "1.0"
      06                                # unsigned(6)
      A2                                # map(2)
         00                             # unsigned(0)
         01                             # unsigned(1)
         01                             # unsigned(1)
         05                             # unsigned(5)
      07                                # unsigned(7)
      A2                                # map(2)
         00                             # unsigned(0)
         19 0ED8                        # unsigned(3800)
         01                             # unsigned(1)
         19 1388                        # unsigned(5000)
      08                                # unsigned(8)
      A2                                # map(2)
         00                             # unsigned(0)
         18 7D                          # unsigned(125)
         01                             # unsigned(1)
         19 0384                        # unsigned(900)
      09                                # unsigned(9)
      18 64                             # unsigned(100)
      0A                                # unsigned(10)
      0F                                # unsigned(15)
      0B                                # unsigned(11)
      A1                                # map(1)
         00                             # unsigned(0)
         00                             # unsigned(0)
      0D                                # unsigned(13)
      1A 5182428F                       # unsigned(1367491215)
      0E                                # unsigned(14)
      66                                # text(6)
         2B30323A3030                   # "+02:00"
      10                                # unsigned(16)
      61                                # text(1)
         55                             # "U"
```

The same example using the LwM2M CBOR diagnostic notation is shown below.

```
{[3, 0]: {0: "Open Mobile Alliance",
          1: "Lightweight M2M Client",
          2: "345000123",
          3: "1.0",
          6: {0: 1,
              1: 5},
          7: {0: 3800,
              1: 5000},
          8: {0: 125,
              1: 900},
          9: 100,
          10: 15,
          11: {0: 0},
          13: 1367491215,
          14: "+02:00",
          16: "U"}}
```

##### Multiple Object Instances Example

A request to the LwM2M Server Object (Read /1) of the LwM2M example client would return the following LwM2M CBOR payload. This example has a size of 63 bytes.

```
A1                   # map(1)
   01                # unsigned(1)
   A2                # map(2)
      00             # unsigned(0)
      A7             # map(7)
         00          # unsigned(0)
         18 65       # unsigned(101)
         01          # unsigned(1)
         1A 00015180 # unsigned(86400)
         02          # unsigned(2)
         19 012C     # unsigned(300)
         03          # unsigned(3)
         19 1770     # unsigned(6000)
         05          # unsigned(5)
         1A 00015180 # unsigned(86400)
         06          # unsigned(6)
         F5          # primitive(21)
         07          # unsigned(7)
         61          # text(1)
            55       # "U"
      01             # unsigned(1)
      A7             # map(7)
         00          # unsigned(0)
         18 66       # unsigned(102)
         01          # unsigned(1)
         1A 00015180 # unsigned(86400)
         02          # unsigned(2)
         19 0258     # unsigned(600)
         03          # unsigned(3)
         19 1770     # unsigned(6000)
         05          # unsigned(5)
         1A 00015180 # unsigned(86400)
         06          # unsigned(6)
         F4          # primitive(20)
         07          # unsigned(7)
         61          # text(1)
            55       # "U"
```

The same example using the CBOR diagnostic notation is shown below.

```
{1: {0: {0: 101,
         1: 86400,
         2: 300,
         3: 6000,
         5: 86400,
         6: true,
         7: "U"},
     1: {0: 102,
         1: 86400,
         2: 600,
         3: 6000,
         5: 86400,
         6: false,
         7: "U"}}}
```

##### Composite Operation Example

A composite request to the manufacturer name (/3/0/0), battery level(/3/0/9), and registration lifetime (/1/0/1) of the LwM2M example client would return the following LwM2M CBOR payload. This example has a size of 39 bytes.

    A2                                      # map(2)
       82                                   # array(2)
          03                                # unsigned(3)
          00                                # unsigned(0)
       A2                                   # map(2)
          00                                # unsigned(0)
          74                                # text(20)
             4F70656E204D6F62696C6520416C6C69616E6365 # "Open Mobile Alliance"
          09                                # unsigned(9)
          18 64                             # unsigned(100)
       83                                   # array(3)
          01                                # unsigned(1)
          00                                # unsigned(0)
          01                                # unsigned(1)
       1A 00015180                          # unsigned(86400)
The same example using the CBOR diagnostic notation is shown below.

```
{[3, 0]: {0: "Open Mobile Alliance",
          9: 100},
 [1, 0, 1]: 86400}
```

#### TLV

For "Read" and "Write" operations, the binary TLV (Type-Length-Value) format can be used to represent an array of values or a singular value using a compact binary representation, which is easy to process on simple embedded devices. The format has a minimum overhead per value of just 2 bytes and a maximum overhead of 5 bytes depending on the type of Identifier and length of the value. The maximum size of an Object Instance or Resource in this format is 16.7 MB. The format is self-describing, thus a parser can skip TLVs for which the Resource is not known.

This data format has a Media Type of application/vnd.oma.lwm2m+tlv.
{:page-break}
The format is an array of the following byte sequence, where each array entry represents an Object Instance, Resource, or Resource Instance:

<table>
    <caption>TLV format and description</caption>
    <thead>
        <tr>
            <th>Field</th>
            <th>Format and Length</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="4">Type</td>
            <td rowspan="4">8-bits masked field:<br><br>0bxxxxxxxx (MSB is the bit following 0b)<br><br>Bit numbering is 0 for the LSB to 7 for the MSB</td>
            <td> Bits 7-6: Indicates the type of Identifier.<br><br>00= Object Instance in which case the Value contains one or more Resource TLVs<br><br>01= Resource Instance with Value for use within a multiple Resource TLV<br><br>10= multiple Resource, in which case the Value contains one or more Resource Instance TLVs<br><br>11= Resource with Value</td>
        </tr>
        <tr>
            <td>Bit 5: Indicates the Length of the Identifier.<br><br>0=The Identifier field of this TLV is 8 bits long<br><br>1=The Identifier field of this TLV is 16 bits long</td>
        </tr>
        <tr>
            <td>Bit 4-3: Indicates the type of Length.<br><br>00=No length field, the value immediately follows the Identifier field in is of the length indicated by Bits 2-0 of this field<br><br>01 = The Length field is 8-bits and Bits 2-0 MUST be ignored<br><br>10 = The Length field is 16-bits and Bits 2-0 MUST be ignored<br><br>11 = The Length field is 24-bits and Bits 2-0 MUST be ignored</td>
        </tr>
        <tr>
            <td>Bits 2-0: A 3-bit unsigned integer indicating the Length of the Value.</td>
        </tr>
        <tr>
            <td>Identifier</td>
            <td>8-bit or 16-bit unsigned integer as indicated by the Type field.</td>
            <td>The Object Instance, Resource, or Resource Instance ID as indicated by the Type field.</td>
        </tr>
        <tr>
            <td>Length</td>
            <td>0-24-bit unsigned integer as indicated by the Type field.</td>
            <td>The Length of the following field in bytes.</td>
        </tr>
        <tr>
            <td>Value</td>
            <td>Sequence of bytes of Length</td>
            <td>Value of the tag. The format of the value depends on the Resource's data type (See <a href="">Data Types (Normative)</a>).</td>
        </tr>
    </tbody>
</table>

Each TLV entry starts with a Type byte that indicates if the TLV contains an Object Instance, a Resource, multiple Resources, or a Resource Instance. Object Instance and Resource with Resource Instance TLVs contains other TLVs in their value. The hierarchy is as follows and may be up to 3 levels deep.

-   Object Instance TLV, which contains

    -   Resource TLVs or

    -   multiple Resource TLVs, which contains

        -   Resource Instance TLVs

For simplicity and to prevent any ambiguity on Object Instance Identity, when the Object Instance ID is not specified in the request, the Object Instance TLV MUST be used, whatever the number of Object Instances (1 or more) to return to the LwM2M Server. When the Object Instance ID is specified in the request, the Object Instance TLV is optional.

When a Multiple Resource has to be returned to the LwM2M Server, the Multiple Resource TLV MUST be used whatever the number of Instances (0, 1 or more) of that resource.

[Figure TLV nesting]() illustrates the possible nesting of Object Instance, Resource, multiple Resources, and Resource Instance TLVs. One or several Resource TLVs, and/or one or several multiple Resource TLVs MAY be nested in an Object Instance TLV. A multiple Resource TLV contains one or several Resource Instance TLVs.

<figure class="text-center">
      <img src="images/tlv_nesting.svg" alt="TLV nesting">
      <figcaption>TLV nesting</figcaption>
</figure>

##### Single Object Instance Request Example

In this example, a request for the Device Object Instance (ID:3) of an LwM2M client is made (Read /3/0). The client responds with a TLV payload including all of the readable Resources. This TLV payload would have the following format. The total payload size with the TLV encoding is 121 bytes:
```
C8 00 14 4F 70 65 6E 20 4D 6F 62 69 6C 65 20 41 6C 6C 69 61 6E 63 65
C8 01 16 4C 69 67 68 74 77 65 69 67 74 20 4D 32 4D 20 43 6C 69 65 6E 74
C8 02 09 33 34 35 30 30 30 31 32 33
C3 03 31 2E 30
86 06
   41 00 01
   41 01 05
88 07 08
   42 00 0E D8
   42 01 13 88
87 08
   41 00 7D
   42 01 03 84
C1 09 64
C1 0A 0F
83 0B
   41 00 00
C4 0D 51 82 42 8F
C6 0E 2B 30 32 3A 30 30
C1 10 55
```

<table>
    <caption>Single Object Instance Request Example</caption>
    <thead>
        <tr>
            <th>TLV</th>
            <th>Type Byte</th>
            <th>ID Byte(s)</th>
            <th>Length Byte(s)</th>
            <th>Value</th>
            <th>Total Bytes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Manufacturer Resource</td>
            <td>0b11 0 01 000</td>
            <td>0x00</td>
            <td>0x14 (20 bytes)</td>
            <td>Open Mobile Alliance [String]</td>
            <td>23</td>
        </tr>
        <tr>
            <td>Model Number</td>
            <td>0b11 0 01 000</td>
            <td>0x01</td>
            <td>0x16 (22 bytes)</td>
            <td>"Lightweight M2M Client" [String]</td>
            <td>25</td>
        </tr>
        <tr>
            <td>Serial Number</td>
            <td>0b11 0 01 000</td>
            <td>0x02</td>
            <td>0x09 (9 bytes)</td>
            <td>"345000123" [String]</td>
            <td>12</td>
        </tr>
        <tr>
            <td>Firmware Version</td>
            <td>0b11 0 00 011</td>
            <td>0x03</td>
            <td>─</td>
            <td>"1.0" [String] (3 bytes)</td>
            <td>5</td>
        </tr>
        <tr>
            <td>Available Power Sources</td>
            <td>0b10 0 00 110</td>
            <td>0x06</td>
            <td>─</td>
            <td>The next two rows (6 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td>Available Power Sources[0]</td>
            <td>0b01 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0X01 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Available Power Sources[1]</td>
            <td>0b01 0 00 001</td>
            <td>0x01</td>
            <td>─</td>
            <td>0X05 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Power Source Voltage</td>
            <td>0b10 0 01 000</td>
            <td>0x07</td>
            <td>0x08 (8 bytes)</td>
            <td>The next two rows</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Power Source Voltage[0]</td>
            <td>0b01 0 00 010</td>
            <td>0x00</td>
            <td>─</td>
            <td>0X0ED8 [16-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Power Source Voltage[1]</td>
            <td>0b01 0 00 010</td>
            <td>0x01</td>
            <td>─</td>
            <td>0X1388 [16-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Power Source Current</td>
            <td>0b10 0 00 111</td>
            <td>0x08</td>
            <td>─</td>
            <td>The next two rows (7 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td>Power Source Current[0]</td>
            <td>0b01 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0X7D [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Power Source Current[1]</td>
            <td>0b01 0 00 010</td>
            <td>0x01</td>
            <td>─</td>
            <td>0X0384 [16-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Battery Level</td>
            <td>0b11 0 00 001</td>
            <td>0x09</td>
            <td>─</td>
            <td>0x64 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Memory Free</td>
            <td>0b11 0 00 001</td>
            <td>0x0A</td>
            <td>─</td>
            <td>0x0F [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Error Code</td>
            <td>0b10 0 00 011</td>
            <td>0x0B</td>
            <td>─</td>
            <td>The next row (3 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td>Error Code[0]</td>
            <td>0b01 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0x00 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Current Time</td>
            <td>0b11 0 00 100</td>
            <td>0x0D</td>
            <td>─</td>
            <td>0x5182428F [32-bit Integer]</td>
            <td>6</td>
        </tr>
        <tr>
            <td>UTC Offset</td>
            <td>0b11 0 00 110</td>
            <td>0x0E</td>
            <td>─</td>
            <td>"+02:00" [String] (6 bytes)</td>
            <td>8</td>
        </tr>
        <tr>
            <td>Supported Binding and Modes</td>
            <td>0b11 0 00 001</td>
            <td>0x10</td>
            <td>─</td>
            <td>"U" [String] (1 byte)</td>
            <td>3</td>
        </tr>
        <tr>
            <td><strong>Total</strong></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>121</td>
        </tr>
    </tbody>
</table>

##### Multiple Object Instance Request Examples

A)  Request on Single-Instance Object

In this example, a request for the Device Object Instance (ID:3) of an LwM2M client is made (Read /3). The Device Object is a Single-Instance Object, but the Object Instance TLV is used (to be compared with the example of the previous section).

The client responds with a TLV payload including the Object Instance ID and all its readable Resources. This TLV payload would have the following value (indented for readability) and format. The total payload size with the TLV encoding is 124 bytes:
```
08 00 79
   C8 00 14 4F 70 65 6E 20 4D 6F 62 69 6C 65 20 41 6C 6C 69 61 6E 63 65
   C8 01 16 4C 69 67 68 74 77 65 69 67 74 20 4D 32 4D 20 43 6C 69 65 6E 74
   C8 02 09 33 34 35 30 30 30 31 32 33
   C3 03 31 2E 30
   86 06
      41 00 01
      41 01 05
88 07 08
   42 00 0E D8
   42 01 13 88
87 08
   41 00 7D
   42 01 03 84
C1 09 64
C1 0A 0F
83 0B
   41 00 00
C4 0D 51 82 42 8F
C6 0E 2B 30 32 3A 30 30
C1 10 55
```
{:page-break}

<table>
    <caption>Request on Single-Instance Object</caption>
    <thead>
        <tr>
            <th>TLV</th>
            <th>Type Byte</th>
            <th>ID Byte(s)</th>
            <th>Length Byte(s)</th>
            <th>Value</th>
            <th>Total Bytes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>Device Object Instance 0</strong></td>
            <td><strong>0b00 0 01 000</strong></td>
            <td><strong>0x00</strong></td>
            <td><strong>0x79 (121 bytes)</strong></td>
            <td><strong>The next 20 rows</strong></td>
            <td><strong>3</strong></td>
        </tr>
        <tr>
            <td>Manufacturer Resource</td>
            <td>0b11 0 01 000</td>
            <td>0x00</td>
            <td>0x14 (20 bytes)</td>
            <td>Open Mobile Alliance [String]</td>
            <td>23</td>
        </tr>
        <tr>
            <td>Model Number</td>
            <td>0b11 0 01 000</td>
            <td>0x01</td>
            <td>0x16 (22 bytes)</td>
            <td>"Lightweight M2M Client" [String]</td>
            <td>25</td>
        </tr>
        <tr>
            <td>Serial Number</td>
            <td>0b11 0 01 000</td>
            <td>0x02</td>
            <td>0x09 (9 bytes)</td>
            <td>"345000123" [String]</td>
            <td>12</td>
        </tr>
        <tr>
            <td>Firmware Version</td>
            <td>0b11 0 00 011</td>
            <td>0x03</td>
            <td>─</td>
            <td>"1.0" [String] (3 bytes)</td>
            <td>5</td>
        </tr>
        <tr>
            <td>Available Power Sources</td>
            <td>0b10 0 00 110</td>
            <td>0x06</td>
            <td>─</td>
            <td>The next two rows (6 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td>Available Power Sources[0]</td>
            <td>0b01 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0X01 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Available Power Sources[1]</td>
            <td>0b01 0 00 001</td>
            <td>0x01</td>
            <td>─</td>
            <td>0X05 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Power Source Voltage</td>
            <td>0b10 0 01 000</td>
            <td>0x07</td>
            <td>0x08 (8 bytes)</td>
            <td>The next two rows</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Power Source Voltage[0]</td>
            <td>0b01 0 00 010</td>
            <td>0x00</td>
            <td>─</td>
            <td>0X0ED8 [16-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Power Source Voltage[1]</td>
            <td>0b01 0 00 010</td>
            <td>0x01</td>
            <td>─</td>
            <td>0X1388 [16-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Power Source Current</td>
            <td>0b10 0 00 111</td>
            <td>0x08</td>
            <td>─</td>
            <td>The next two rows (7 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td>Power Source Current[0]</td>
            <td>0b01 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0X7D [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Power Source Current[1]</td>
            <td>0b01 0 00 010</td>
            <td>0x01</td>
            <td>─</td>
            <td>0X0384 [16-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Battery Level</td>
            <td>0b11 0 00 001</td>
            <td>0x09</td>
            <td>─</td>
            <td>0x64 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Memory Free</td>
            <td>0b11 0 00 001</td>
            <td>0x0A</td>
            <td>─</td>
            <td>0x0F [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Error Code</td>
            <td>0b10 0 00 011</td>
            <td>0x0B</td>
            <td>─</td>
            <td>The next row (3 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td>Error Code[0]</td>
            <td>0b01 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0x00 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Current Time</td>
            <td>0b11 0 00 100</td>
            <td>0x0D</td>
            <td>─</td>
            <td>0x5182428F [32-bit Integer]</td>
            <td>6</td>
        </tr>
        <tr>
            <td>UTC Offset</td>
            <td>0b11 0 00 110</td>
            <td>0x0E</td>
            <td>─</td>
            <td>"+02:00" [String] (6 bytes)</td>
            <td>8</td>
        </tr>
        <tr>
            <td>Supported Binding and Modes</td>
            <td>0b11 0 00 001</td>
            <td>0x10</td>
            <td>─</td>
            <td>"U" [String] (1 byte)</td>
            <td>3</td>
        </tr>
        <tr>
            <td><strong>Total</strong></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>124</td>
        </tr>
    </tbody>
</table>

B)  Request on Multiple-Instance Object having 2 instances

In this example, a request on the Access Control Object (ID:2) of an LwM2M client is made (Read /2). The Access Control Object is a Multiple-Instance Object. In this simplified example, it has only 2 instances describing the access rights of two LwM2M Servers with Short IDs 127 and 310 on Objects Instances /1/0 and /3/0.

{:page-break}

The client responds with a TLV payload including the 2 Object Instances (ID:0 and ID:2) and their Resources. This TLV payload would have the following value (indented for readability) and format. The total payload size with the TLV encoding is 38 bytes:
```
08 00 0E
   C1 00 01
   C1 01 00
   83 02
      41 7F 07
   C1 03 7F
08 02 12
   C1 00 03
   C1 01 00
   87 02
      41 7F 07
      61 01 36 01
   C1 03 7F
```
<table>
    <caption>Request on Multiple-Instance Object having 2 instances</caption>
    <thead>
        <tr>
            <th>TLV</th>
            <th>Type Byte</th>
            <th>ID Byte(s)</th>
            <th>Length Byte(s)</th>
            <th>Value</th>
            <th>Total Bytes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>Access Control Object Instance 0</strong></td>
            <td><strong>0b00 0 01 000</strong></td>
            <td><strong>0x00</strong></td>
            <td><strong>0x0E (17 bytes)</strong></td>
            <td><strong>The next 5 rows</strong></td>
            <td><strong>3</strong></td>
        </tr>
        <tr>
            <td>Object ID</td>
            <td>0b11 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0x01 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>0b11 0 00 001</td>
            <td>0x01</td>
            <td>─</td>
            <td>0x00 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ACL</td>
            <td>0b10 0 00 011</td>
            <td>0x02</td>
            <td>─</td>
            <td>The next row (3 bytes)</td>
            <td>2</td>
        </tr>
        <tr>
            <td><em>ACL [127]</em></td>
            <td><em>0b01 0 00 001</em></td>
            <td><em>0x7F</em></td>
            <td>─</td>
            <td><em>0b000 00111</em> [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Access Control Owner</td>
            <td>0b11 0 00 001</td>
            <td>0x03</td>
            <td>─</td>
            <td>0x7F [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td><strong>Access Control Object Instance 2</strong></td>
            <td><strong>0b00 0 01 000</strong></td>
            <td><strong>0x02</strong></td>
            <td><strong>0x12 (18 bytes)</strong></td>
            <td><strong>The next 6 rows</strong></td>
            <td><strong>3</strong></td>
        </tr>
        <tr>
            <td>Object ID</td>
            <td>0b11 0 00 001</td>
            <td>0x00</td>
            <td>─</td>
            <td>0x03 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Object Instance ID</td>
            <td>0b11 0 00 001</td>
            <td>0x01</td>
            <td>─</td>
            <td>0x00 [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td>ACL</td>
            <td>0b10 0 00 111</td>
            <td>0x02</td>
            <td>─</td>
            <td>The next 2 rows</td>
            <td>2</td>
        </tr>
        <tr>
            <td><em>ACL [127]</em></td>
            <td><em>0b01 0 00 001</em></td>
            <td><em>0x7F</em></td>
            <td>─</td>
            <td><em>0b000 00111</em> [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td><em>ACL [310]</em></td>
            <td><em>0b01 1 00 001</em></td>
            <td><em>0x0136</em></td>
            <td>─</td>
            <td><em>0b000 00001</em> [8-bit Integer]</td>
            <td>4</td>
        </tr>
        <tr>
            <td>Access Control Owner</td>
            <td>0b11 0 00 001</td>
            <td>0x03</td>
            <td>─</td>
            <td>0x7F [8-bit Integer]</td>
            <td>3</td>
        </tr>
        <tr>
            <td><strong>Total</strong></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>38</td>
        </tr>
    </tbody>
</table>


C)  Request on Multiple-Instance Object having 1 instance only

In this example, a request to the Server Object Instances of an LwM2M client is performed (Read /1). The Server Object is a Multiple-Instances Object. The client has only one Server Object instance and will respond with a TLV payload including the single Object Instance (0) and their Resources. This TLV payload would have the following value (indented for readability) and format. The total payload size with the TLV encoding is 18 bytes:
```
08 00 0D
   C1 00 01
   C4 01 00 01 51 80
   C1 06 01
   C1 07 55
```

{:page-break}

<table>
    <caption>Example, a request to the Server Object Instances of an LwM2M client is performed (Read /1)</caption>
    <thead>
    <tr>
        <th>TLV</th>
        <th>Type Byte</th>
        <th>ID Byte(s)</th>
        <th>Length Byte(s)</th>
        <th>Value</th>
        <th>Total Bytes</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><strong>Server Object Instance 0</strong></td>
        <td><strong>0b00 0 01 000</strong></td>
        <td><strong>0x00</strong></td>
        <td><strong>0x0D <br> (13 Bytes)</strong></td>
        <td><strong>The next 5 rows</strong></td>
        <td><strong>3</td>
    </tr>
    <tr>
        <td> Short Server ID </td>
        <td> 0b11 0 00 001 </td>
        <td> 0x00 </td>
        <td> ─ </td>
        <td> 0x01 [8-bit Integer] </td>
        <td> 2 </td>
    </tr>
    <tr>
        <td> Lifetime </td>
        <td> 0b11 0 00 100 </td>
        <td> 0x01  </td>
        <td> ─ </td>
        <td> 86400 [32-bit Integer] </td>
        <td> 5 </td>
    </tr>
    <tr>
        <td> Notification Storing When Disabled or Offline </td>
        <td> 0b11 0 00 001 </td>
        <td> 0x06  </td>
        <td> ─  </td>
        <td> True [Boolean] </td>
        <td> 3 </td>
    </tr>
    <tr>
        <td> Binding </td>
        <td> 0b11 0 00 001 </td>
        <td> 0x07 </td>
        <td> ─     </td>
        <td> "U" [String] (1 byte) </td>
        <td> 3 </td>
    </tr>
    <tr>
        <td colspan="5"> <strong> Total </strong> </td>
        <td> 16 </td>
    </tr>
    </tbody>
</table>

##### Example of Request on an Object Instance containing an Object Link Resource

Examples are based on the LwM2M Object Tree illustration presented in [Figure Object link Resource simple illustration](). The TLV format doesn't report the object hierarchy.

Example 1) request to Object 65 Instance 0: Read /65/0
```
88 00 0C
   44 00 00 42 00 00
   44 01 00 42 00 01
C8 01 0D 38 36 31 33 38 30 30 37 35 35 35 30 30
C4 02 12 34 56 78
```
<table>
    <caption>Example 1) Request to Object 65 Instance 0: Read /65/0</caption>
    <thead>
        <tr>
            <th>TLV</th>
            <th>Type Byte</th>
            <th>ID Byte(s)</th>
            <th>Length Byte(s)</th>
            <th>Value</th>
            <th>Total Bytes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Res 0 lnk</td>
            <td>0b1 0 0 01000</td>
            <td>0x00</td>
            <td>0x0C(12 bytes)</td>
            <td>The next 2 rows</td>
            <td>3</td>
        </tr>
        <tr>
            <td>Res 0 lnk [0]</td>
            <td>0b01 000 100</td>
            <td>0x00</td>
            <td>─</td>
            <td>0x0042 0000 [Objlnk] (66:0)</td>
            <td>6</td>
        </tr>
        <tr>
            <td>Res 0 lnk [1]</td>
            <td>0b01 0 00 100</td>
            <td>0x01</td>
            <td>─</td>
            <td>0x0042 0001 [Objlnk] (66:1)</td>
            <td>6</td>
        </tr>
        <tr>
            <td>Res 1</td>
            <td>0b11 0 01 000</td>
            <td>0x01</td>
            <td>0x0D</td>
            <td>"8613800755500" [String] (13 bytes)</td>
            <td>16</td>
        </tr>
        <tr>
            <td>Res 2</td>
            <td>0b11 0 00 100</td>
            <td>0x02</td>
            <td>─</td>
            <td>0x12345678 [32-bit Integer]</td>
            <td>6</td>
        </tr>
        <tr>
            <td><strong>Total</strong></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>37</td>
        </tr>
    </tbody>
</table>

{:page-break}

Example 2) request to Object 66: Read /66: TLV payload will contain 2 Object Instances
```
08 00 23
   C8 00 0B 6D 79 53 65 72 76 69 63 65 20 31
   C8 01 0F 49 6E 74 65 72 6E 65 74 2E 31 35 2E 32 33 34
   C4 02 00 43 00 00
08 01 23
   C8 00 0B 6D 79 53 65 72 76 69 63 65 20 32
   C8 01 0F 49 6E 74 65 72 6E 65 74 2E 31 35 2E 32 33 35
   C4 02 FF FF FF FF
```
<table>
    <caption>Example 2) request to Object 66: Read /66: TLV payload will contain 2 Object Instances</caption>
    <tbody>
        <tr>
            <th>TLV</th>
            <th>Type Byte</th>
            <th>ID Byte(s)</th>
            <th>Length Byte(s)</th>
            <th>Value</th>
            <th>Total Bytes</th>
        </tr>
        <tr>
            <td><strong>Object 66 Instance 0</strong></td>
            <td><strong>0b00 0 01 000</strong></td>
            <td><strong>0x00</strong></td>
            <td><strong>0x23 (35 bytes)</strong></td>
            <td><strong>The next 3 rows</strong></td>
            <td>3</td>
        </tr>
        <tr>
            <td>Res 0</td>
            <td>0b11 0 01 000</td>
            <td>0x00</td>
            <td>0x0B</td>
            <td>"myService 1" [String] (11 bytes)</td>
            <td>14</td>
        </tr>
        <tr>
            <td>Res 1</td>
            <td>0b11 0 01 000</td>
            <td>0x01</td>
            <td>0x0F</td>
            <td>"Internet.15.234" [String] (15 bytes)</td>
            <td>15</td>
        </tr>
        <tr>
            <td>Res 2 lnk</td>
            <td>0b11 0 00 100</td>
            <td><em>0x02</em></td>
            <td>─</td>
            <td>0x0043 0000 [Objlnk] (67:0)</td>
            <td>6</td>
        </tr>
        <tr>
            <td><strong>Object 66 Instance 1</strong></td>
            <td><strong>0b00 0 01000</strong></td>
            <td><strong>0x01</strong></td>
            <td><strong>0x23 (35 bytes)</strong></td>
            <td><strong>The next 3 rows</strong></td>
            <td><strong>3</strong></td>
        </tr>
        <tr>
            <td>Res 0</td>
            <td>0b11 0 01 000</td>
            <td>0x00</td>
            <td>0x0B</td>
            <td>"myService 2" [String] (11 bytes)</td>
            <td>14</td>
        </tr>
        <tr>
            <td>Res 1</td>
            <td>0b11 0 00 000</td>
            <td>0x01</td>
            <td>0x0F</td>
            <td>"Internet.15.235" [String] (15 bytes)</td>
            <td>15</td>
        </tr>
        <tr>
            <td>Res 2 lnk</td>
            <td>0b11 0 00 100</td>
            <td>0x02</td>
            <td>─</td>
            <td>0xFFFF FFFF [Objlnk] (no link)</td>
            <td>6</td>
        </tr>
        <tr>
            <td><strong>Total</strong></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>76</td>
        </tr>
    </tbody>
</table>

#### SenML JSON

When an LwM2M Client is supporting the SenML JSON data format and the format is used to transport Object Instance(s), multiple resource and single resource values for both "Read" and "Write" operations, SenML JSON payload MUST use the format defined in this section. This format MAY be used also for transporting a single value of a Resource.

The format MUST comply to \[SENML\] JSON representation extended for supporting LwM2M Object Link data type and MUST support all attributes defined in [Table SenML JSON format and description]().

According to \[SENML\] semantics, the SenML JSON data format is composed of an array of entries (SenML Records) with optional and mandatory fields.

Each entry of the SenML JSON format is a Resource Instance, where the Name attribute need to be prepended by the Base Name attribute to form the unique identifier of this Resource instance.

The Name attribute in an entry is a URI path relative to the Base Name; namely the Name attribute could simply be the full URI path of a requested Resource Instance when Base Name is absent.

The SenML JSON format is useful for transporting multiple Resource Instances for example when transporting all Instances of an Object with all Resources, and Resource Instances within a single LwM2M Client response.

In particular, when Base Name is set to the LwM2M Object root (e.g. "/"), the SenML JSON format may support to return a hierarchy of Object Instances when Object Link datatype resources are reported (example given below). The resource instances tree report is performed in using a Breadth-First traversal strategy (see SenML JSON second example below); a given Object Instance MUST appear at most once in that report. The SenML JSON format also includes optional time fields, which allows for multiple versions of representations to be sent in the same payload or indicating the time when the representation was created (e.g., measurement made).

Note: SenML time values (Base Time and Time) are represented in floating point as seconds and a missing time attribute is considered to have a value of zero. Base time and time are added together. In general, positive time values represent an absolute time relative to the Unix epoch, while negative values represent a relative time in the past from the current time. For details see \[SENML\].

Historical version of notifications are typically generated when "Notification Storing When Disabled or Offline" resource of the LwM2M Server Object is set to true (see [LwM2M Objects defined by OMA (Normative)]()) and when the Device comes on line after having been disabled for a period of time.

The SenML JSON data format has a Media Type application/senml+json.

\[LwM2M-TS\_1.0\] defined the format for application/vnd.oma.lwm2m+json based on an early draft version of SenML. \[LwM2M-TS\_1.1\] aligned the SenML JSON format with the final version of the SenML specification. However, SenML specification does not define the necessary semantics for its use with LwM2M Read-Composite or Write-Composite operations. This issue was partially resolved by \[LwM2M-TS\_1.1\] and since its publication, \[RFC8790\] has formally defined application/senml-etch+json and application/senml-etch+cbor media types and their semantics in line with what was specified in \[LwM2M-TS\_1.1\]. 

For backward compatibility, server implementations of \[LwM2M-TS\_1.1\] MUST support both application/senml+json and application/vnd.oma.lwm2m+json. Client implementations of \[LwM2M-TS\_1.1\] and later MUST NOT use the application/vnd.oma.lwm2m+json format. Furthermore, clients implementing LwM2M TS 1.2 or later that support READ-Composite and/or Write-Composite operations MUST also support either application/senml-etch+json, or application/senml-etch+cbor.

<table>
    <caption>SenML JSON format and description</caption>
    <thead>
        <tr>
            <th>Attributes</th>
            <th>JSON Variable</th>
            <th>Mandatory?</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Base Name</td>
            <td>bn</td>
            <td>No</td>
            <td>The base name string which is prepended to the Name value of the entry for forming a globally unique identifier for the resource.</td>
        </tr>
        <tr>
            <td>Base Time</td>
            <td>bt</td>
            <td>No</td>
            <td>The base time which the Time values are relative to.</td>
        </tr>
        <tr>
            <td>Name</td>
            <td>n</td>
            <td>No</td>
            <td>The Name value is prepended by the Base Name value to form the name of the resource instance. The resulting name uniquely identifies the Resource Instance from all others.
                Example:<br>
                • if Base Name is "/" , the Array entry Name of the Resource is {Object}/{Object Instance}/{Resource}/{Resource Instance}<br>
                • When Base Name is not present, the Array entry Name is the full URI of the requested Resource Instance
            </td>
        </tr>
        <tr>
            <td>Time</td>
            <td>t</td>
            <td>No</td>
            <td>The time of the representation relative to the Base Time in seconds for a notification. Required only for historical representations.</td>
        </tr>
        <tr>
            <td>Float Value</td>
            <td>v</td>
            <td rowspan="5">One value field is mandatory</td>
            <td>Value as a JSON float if the Resource data type is Integer, Float, or Time.</td>
        </tr>
        <tr>
            <td>Boolean Value</td>
            <td>vb</td>
            <td>Value as a JSON Boolean if the Resource data type is boolean.</td>
        </tr>
        <tr>
            <td>Object Link Value</td>
            <td>vlo</td>
            <td>Value as a JSON string if the Resource data type is Objlnk.<br>
                Format according to <a href="">Data Types (Normative)</a> (e.g. "10:03").</td>
        </tr>
        <tr>
            <td>Opaque Value</td>
            <td>vd</td>
            <td>For Resource data type "opaque" this holds the Base64 encoded representation of the Resource.</td>
        </tr>
        <tr>
            <td>String Value</td>
            <td>vs</td>
            <td>Value as a JSON string for all other Resource data types.</td>
        </tr>
    </tbody>
</table>

For example, a request to a Device Object (Read /3/0) of the LwM2M example client would return the following SenML JSON payload. This example has a size of 399 bytes.

<table>
    <caption>SenML JSON payload returned from example request to Device Object (Read /3/0)</caption>
    <tr>
        <td>
            [{"bn":"/3/0/","n":"0","vs":"Open Mobile Alliance"},<br>
            {"n":"1","vs":"Lightweight M2M Client"},<br>
            {"n":"2","vs":"345000123"},<br>
            {"n":"3","vs":"1.0"},<br>
            {"n":"6/0","v":1},<br>
            {"n":"6/1","v":5},<br>
            {"n":"7/0","v":3800},<br>
            {"n":"7/1","v":5000},<br>
            {"n":"8/0","v":125},<br>
            {"n":"8/1","v":900},<br>
            {"n":"9","v":100},<br>
            {"n":"10","v":15},<br>
            {"n":"11/0","v":0},<br>
            {"n":"13","v":1367491215},<br>
            {"n":"14","vs":"+02:00"},<br>
            {"n":"16","vs":"U"}]<br>
        </td>
    </tr>
</table>

For example, a notification about a Resource containing multiple historical representations of a Temperature Resource (ID:2) (e.g. Instance ID:1 of hypothetical Object ID 72) could result in the following SenML JSON payload:

<table>
    <caption>SenML JSON payload from example notification about a Resource containing multiple historical representations of a Temperature Resource</caption>
    <tr>
        <td>
            [{"bn":"/72/","bt":25462634,"n":"1/2","v":22.4,"t":-5},<br>
            {"n":"1/2","v":22.9,"t":-30},<br>
            {"n":"1/2","v":24.1,"t":-50}]<br>
        </td>
    </tr>
</table>

For example, a request to Object 65 of the LwM2M example seen in [Figure Object link Resource simple illustration]() (Read /65/0) would return the following SenML JSON payload.

Because the Base Name is specified, the full hierarchy linked to the Instance 0 of Object 65 can be reported in a single response (Object 66 Instance 0 & 1, and Instance 0 of Object 67 are part of the payload). This example has a size of 412 bytes.

<table>
    <caption>SenML JSON payload returned from example request to Object 65 of the LwM2M example seen on <a href="">Figure Object link Resource simple illustration</a> (Read /65/0)</caption>
    <tr>
        <td>
            [{"bn":"/","n":"65/0/0/0","vlo":"66:0"},<br>
            {"n":"65/0/0/1","vlo":"66:1"},<br>
            {"n":"65/0/1","vs":"8613800755500"},<br>
            {"n":"65/0/2","v":1},<br>
            {"n":"66/0/0","vs":"myService1"},<br>
            {"n":"66/0/1","vs":"Internet.15.234"},<br>
            {"n":"66/0/2","vlo":"67:0"},<br>
            {"n":"66/1/0","vs":"myService2"},<br>
            {"n":"66/1/1","vs":"Internet.15.235"},<br>
            {"n":"66/1/2","vlo":"FFFF:FFFF"},<br>
            {"n":"67/0/0","vs":"85.76.76.84"},<br>
            {"n":"67/0/1","vs":"85.76.255.255"}]<br>
        </td>
    </tr>
</table>

For example, a request to Device Object on Resource 0 of the LwM2M example client (Read /3/0/0) could return the following SenML JSON payload.

<table>
    <caption>SenML JSON payload returned from example request to Device Object on Resource 0 of the LwM2M example client (Read /3/0/0)</caption>
    <tr>
        <td>
            [{"bn":"/3/0/0","vs":"Open Mobile Alliance}]<br>
        </td>
    </tr>
</table>

For example, a Read-Composite operation from an LwM2M Server to the LwM2M client to read manufacturer name and battery level from the LwM2M Device Object together with the registration lifetime Resource from the LwM2M Server Object will look as follows:
<table>
    <caption>SenML JSON payload in the server request to read manufacturer name, battery level and registration lifetime</caption>
    <tr>
        <td>
            [{"n":"/3/0/0"},<br>
            {"n":"/3/0/9"},<br>
            {"n":"/1/0/1"}]<br>
        </td>
    </tr>
</table>

In response to the Read-Composite operation above the LwM2M Client will return a SenML JSON payload similar to the one shown below. 
<table>
<caption>SenML JSON payload in the client response to server request to read manufacturer name, battery level and registration lifetime</caption>
    <tr>
        <td>
            [{"n":"/3/0/0", "vs":"Open Mobile Alliance"},<br>
            {"n" :"/3/0/9", "v":95},<br>
            {"n":"/1/0/1", "v":86400}]<br>
        </td>
    </tr>
</table>


For example, a Read-Composite operation from an LwM2M Server to an LwM2M client to read its Location Object together with Network
Bearer, Available Network Bearer and Radio Signal Strength resources in Connectivity Monitoring Object will look as follows:
<table>
    <caption>SenML JSON payload in the server request to read Network Bearer, Available Network Bearer, Radio Signal Strength and Location</caption>
    <tr>
        <td>
            [{"bn":"/4/0/", "n":"0"},<br>
            {"n":"1"},<br>
            {"n":"2"},<br>
            {"bn":"/6/", "n":"0"}]<br>
        </td>
    </tr>
</table>

Note: As shown above, SenML records used with a Read-Composite operation do not contain any value field while the responses will. Prior to \[RFC8790\], this implied the need for SenML parsers to be context aware, i.e. to distinguish between SenML records received in Read-Composite operations and responses to such requests. However, media types, application/senml-etch+json and application/senml-etch+cbor, defined in \[RFC8790\] have removed the requirement for context aware parsing.

For example, a Write-Composite operation by an LwM2M Server to switch off 2 light sources, to dim a 3rd to 20% and to set the thermostat to 18 degrees will have a SenML JSON payload as shown in table below. All lights are controlled by instances of the IPSO Light Control Object (Object ID 3311), while the thermostat is controlled by an instance of the IPSO Set Point Object (Object ID 3308).
<table>
<caption>SenML JSON payload in the server Write-Composite to switch off /3311/0 and /3311/1, while dimming /3311/2 </caption>
    <tr>
        <td>
            [{"n":"/3311/0/5850", "vb":false},<br>
            {"n":"/3311/1/5850", "vb":false},<br>
            {"n":"/3311/2/5851", "v":20},<br>
            {"n":"/3308/0/5900", "v":18}]<br>
        </td>
    </tr>
</table>

Note: The Write-Composite operation with SenML format in \[LwM2M-TS\_1.1\] could only be used to add or replace a Resource in a Multiple-Instance Resource as there was no support for use of a "null" value in a SenML record to indicate the deletion of a specific Resource Instance. The media types, application/senml-etch+json and application/senml-etch+cbor, defined in \[RFC8790\] post LwM2M v1.1 have removed this constraint.

The following example shows a Read-Composite operation from an LwM2M Server to the LwM2M Client to read all objects. This example offers the same functionality as a Read operation for all objects. Note that a response may not return all objects on the LwM2M Client since access control settings have to be taken into account as well. 
<table>
    <caption>SenML JSON payload in the request to all objects</caption>
    <tr>
        <td>
            [{"n":"/"}]<br>
        </td>
    </tr>
</table>

Next we show an example of a Read-Composite operation issued by an LwM2M Server to the LwM2M Client to read all object instances of the LwM2M Server Object. 
<table>
    <caption>SenML JSON payload in the request to all object instances of the LwM2M Server Object</caption>
    <tr>
        <td>
            [{"n":"/1"}]<br>
        </td>
    </tr>
</table>

The final example illustrates how to request all Resources in the first and the third instance of the LwM2M Server Object using a Read-Composite operation issued by an LwM2M Server to the LwM2M Client. 
<table>
    <caption>SenML JSON payload in the request to all resources of the first and third instance of the LwM2M Server Object</caption>
    <tr>
        <td>
            [{"n":"/1/0"},<br>
             {"n":"/1/2"}]<br>
        </td>
    </tr>
</table>

##### LwM2M TS 1.0 JSON format

The JSON format used by \[LwM2M-TS\_1.0\] with media type application/vnd.oma.lwm2m+json is formally defined in \[LwM2M-TS\_1.0\]. The JSON payload shown below is an example reply to a request to the Device Object of the LwM2M example Client ("Read /3/0").

<table>
    <tr>
        <td>
            {"bn":"/3/0/",<br>
            "e":[<br>
            {"n":"0","sv":"Open Mobile Alliance"},<br>
            {"n":"1","sv":"Lightweight M2M Client"},<br>
            {"n":"2","sv":"345000123"},<br>
            {"n":"3","sv":"1.0"},<br>
            {"n":"6/0","v":1},<br>
            {"n":"6/1","v":5},<br>
            {"n":"7/0","v":3800},<br>
            {"n":"7/1","v":5000},<br>
            {"n":"8/0","v":125},<br>
            {"n":"8/1","v":900},<br>
            {"n":"9","v":100},<br>
            {"n":"10","v":15},<br>
            {"n":"11/0","v":0},<br>
            {"n":"13","v":1367491215},<br>
            {"n":"14","sv":"+02:00"},<br>
            {"n":"16","sv":"U"}]<br>
            }<br>
        </td>
    </tr>
</table>

#### SenML CBOR

When an LwM2M Client is supporting the SenML CBOR data format and that format is used to transport Object Instance(s), multiple resource and single resource values for both "Read" and "Write" operations, the SenML CBOR payload MUST use the format defined in Section 6 of \[SENML\]. The same format MAY be used for transporting a single value of a Resource. The object links use a string map key "vlo" also in SenML CBOR representation.

The example from [Table SenML JSON payload returned from example request to Device Object (Read /3/0)]() is shown below in the SenML CBOR format.

```
90 a3 21 65 2f 33 2f 30 2f 00 61 30 03 74 4f 70
65 6e 20 4d 6f 62 69 6c 65 20 41 6c 6c 69 61 6e
63 65 a2 00 61 31 03 76 4c 69 67 68 74 77 65 69
67 68 74 20 4d 32 4d 20 43 6c 69 65 6e 74 a2 00
61 32 03 69 33 34 35 30 30 30 31 32 33 a2 00 61
33 03 63 31 2e 30 a2 00 63 36 2f 30 02 01 a2 00
63 36 2f 31 02 05 a2 00 63 37 2f 30 02 19 0e d8
a2 00 63 37 2f 31 02 19 13 88 a2 00 63 38 2f 30
02 18 7d a2 00 63 38 2f 31 02 19 03 84 a2 00 61
39 02 18 64 a2 00 62 31 30 02 0f a2 00 64 31 31
2f 30 02 00 a2 00 62 31 33 02 1a 51 82 42 8f a2
00 62 31 34 03 66 2b 30 32 3a 30 30 a2 00 62 31
36 03 61 55 
```

For details see [Table SenML JSON payload returned from example request to Device Object (Read /3/0)]().

The same example using the SenML CBOR diagnostic notation is shown below.

```
[{-2: "/3/0/", 0: "0", 3: "Open Mobile Alliance"}, 
{0: "1", 3: "Lightweight M2M Client"}, 
{0: "2", 3: "345000123"}, 
{0: "3", 3: "1.0"}, 
{0: "6/0", 2: 1}, 
{0: "6/1", 2: 5}, 
{0: "7/0", 2: 3800}, 
{0: "7/1", 2: 5000}, 
{0: "8/0", 2: 125}, 
{0: "8/1", 2: 900}, 
{0: "9", 2: 100}, 
{0: "10", 2: 15}, 
{0: "11/0", 2: 0}, 
{0: "13", 2: 1367491215}, 
{0: "14", 3: "+02:00"}, 
{0: "16", 3: "U"}]
```

## Access Control

When an LwM2M Client interacts with multiple LwM2M Servers there is a need to determine which operation on a certain Object or Object Instance is authorized for which LwM2M Server. The Access Control Object has been designed to offer this access management capability. 

An LwM2M Client can be implemented and configured in two ways: 

- In the "Access Control-Enabled" configuration the LwM2M Client is capable of granting access rights to one or several LwM2M Servers.  When an LwM2M Client is connected to multiple LwM2M Servers in this configuration then the Access Control Object MUST be instantiated unless all LwM2M Servers are granted full access rights on all Objects and Object Instances in the LwM2M Client. 

- In the "Access Control-Disabled" configuration the LwM2M Client is only able to interact with a single LwM2M Server. Hence, the capability to manage access rights for multiple LwM2M Servers is not supported, i.e., the Access Control Object is not instantiated. In this configuration the LwM2M Server implicitly has full access rights on all Objects and Object Instances in the LwM2M Client. The Access Control Object need not be instantiated when an LwM2M Client is connected to a single LwM2M Server (i.e., a single LwM2M Server Account exists in the LwM2M Client).

Subsequent sections use the terms "Access Control-Enabled" and "Access Control-Disabled" to refer to these two types of configurations. 

### Access Control Object

#### Access Control Object Overview

In the presence of several LwM2M Servers, there is a need to determine if a certain LwM2M Server is authorized to instantiate a supported Object in the LwM2M Client. Provisioning the necessary authorization policies can only be done by the LwM2M Bootstrap-Server.

Furthermore, the LwM2M Client needs to determine - per supported Object Instance - who the "Access Control Owner" of that Object Instance is and which access rights have been granted to other LwM2M Servers for that Object Instance.

The Access Control Object is specified in Section [LwM2M Object: Access Control]() and examples are presented in [Example LwM2M Client (Informative)]().

#### Access Control Object Management

##### Access Control on Object

To authorize an LwM2M Server to instantiate a certain Object supported by the LwM2M Client, not only an Access Control Object Instance - as defined in Section [Table Access Control on Object]() - MUST be associated to such an Object, but this AC Object Instance MUST also contained an ACL Resource Instance targeting the authorized LwM2M Server.

This kind of Access Control Object Instance associated with a certain Object, MUST only be created or updated during a Bootstrap Phase.  The absence of such an association for a certain Object, prevents this Object to be instantiated by any LwM2M Server.

When such an Access Control Object Instance already exists for a certain Object, this Access Control Object Instance MAY be updated for supporting additional LwM2M Servers; in that case a new ACL Instance per Server is created in that Access Control Object Instance with the Short Server ID of the LwM2M Server as index of this new ACL Instance, and with the "Create" ("C") access right as ACL Resource value.

{:page-break}

<table>
    <caption>Access Control on Object</caption>
    <thead>
    <tr>
        <th>Resource ID</th>
        <th>Resource Name</th>
        <th>Value</th>
    </tr>
    </thead>
    <tbody>
    <tr> 
        <td> 0 </td>
        <td> <strong> Object ID </strong> </td>
        <td> ID of the targeted Object </td> 
    </tr> 
    <tr> 
        <td> 1 </td>
        <td> <strong> Object Instance ID </strong> </td>
        <td> MAX_ID=65535 (meaning: Access Control Object Instance is for the Object Level) </td> 
    </tr>         
    <tr> 
        <td> 2 </td>
        <td> <strong> ACL </strong> </td>
        <td> A Resource Instance per LwM2M Server authorized to instantiate the Object <br> 5<sup>th</sup> LSB: "Create" is only configured </td> 
    </tr>   
    <tr> 
        <td> 3 </td>
        <td> <strong> Access Control Owner </strong> </td>
        <td> MAX_ID=65535 (meaning: managed by Bootstrap Interface) </td> 
    </tr>
    </tbody>
    </table>

##### Access Control on Object Instance

For being able to register which operations MAY be performed on an Object Instance by a certain LwM2M Server, this Object Instance MUST be associated to an Access Control Object Instance as defined in Section [Table Access Control on Object Instance]().

This kind of Access Control Object Instance associated with a certain Object Instance, MAY be created or updated either during a Bootstrap Phase or through the Device Management and Service Enablement Interface.

In particular:

-   when an LwM2M Server creates under authorization an Object Instance (see Section [Authorization]()) in the LwM2M Client, an Access Control Object Instance MUST be created in the LwM2M Client with the Resources values which MUST be set as given in the table just below. The Access Control Owner Resource is configured with the Short Server ID of the LwM2M Server.

<table>
    <caption>Access Control on Object Instance</caption>
    <thead>
        <tr>
            <th>Resource ID</th>
            <th>Resource Name</th>
            <th>Value</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0</td>
            <td><strong>Object ID</strong></td>
            <td>ID of the targeted Object</td>
        </tr>
        <tr>
            <td>1</td>
            <td><strong>Object Instance ID</strong></td>
            <td>ID of the newly created Object Instance</td>
        </tr>
        <tr>
            <td>2</td>
            <td><strong>ACL</strong></td>
            <td>Any combination of the Access Right {none,R,W,E,D} is acceptable (<a href="">LwM2M Object: Access Control</a>)</td>
        </tr>
        <tr>
            <td>3</td>
            <td><strong>Access Control Owner</strong></td>
            <td>The Short Server ID of the LwM2M Server owner of the associated Object Instance</td>
        </tr>
    </tbody>
</table>

-   when this Access Control Object Instance is created during the Bootstrap Phase, ACL(s) and Access Control Owner MUST be set with values respecting the consistency of the LwM2M Client configuration.

-   through the Device Management and Service Enablement Interface, an Access Control Object Instance MUST only be managed by the LwM2M Server declared as the "Access Control Owner" in it.

-   when the LwM2M Server - which is the "Access Control Owner" - adds or modifies (using "Write" operation) access right on the Object Instance for a certain LwM2M Server,

    1.  an ACL Resource having the targeted Short Server ID as ACL Resource Instance ID, has to be instantiated by the LwM2M Client if ACL Resource Instance for the LwM2M Server doesn't exist yet

    2.  the appropriate access right (R,W,D,E) for that targeted Server on the Object Instance has to be set as ACL Resource Instance value

-   A specific ACL Resource Instance MAY be used to grant access rights to LwM2M Servers (except the one defined as the Access Control Owner) which don't have their own ACL Resource Instance. The ID of this ACL Resource Instance containing the default access rights MUST be 0.

-   when an Object Instance is removed via "Delete" operation performed by the LwM2M Server which is the "Access Control Owner", the associated Access Control Object Instance MUST be removed by the LwM2M Client.

[Figure Illustration of the relations between the LwM2M Access Control Object and the other LwM2M Objects]() illustrates the Access Control Management of an Object Instance (/X/2) supported by an LwM2M Client. An Access Control Object Instance (/2/Y) is declared in ② which defines the Access Rights applicable to the Instance 2 of the Object X pointed in ①.

In this Access Control Object Instance ②, 4 Instances of the ACL Resource are defined:

-   ACL Instance 101 contains the operations granted to the Server having 101 as Short ID (Instance ID:2 of the Server Object ID:1 as pointed in ③)

-   ACL Instance 22 contains the operations granted to the Server having 22 as Short ID

-   ACL Instance 31 contains the operations granted to the Server having 31 as Short ID

-   ACL Instance 0 contains the operations granted by default to any Server for which a specific ACL Instance is not defined in this Instance of the Access Control Object (default Access Rights).

This Access Control Object Instance ② also contains a reference to a Server (Access Control Owner) which is the only one Server authorized to manage that Instance of the Access Control Object.

<figure class="text-center">
      <img src="images/relations_access_control_object_other_objects.svg" alt="Illustration of the relations between the LwM2M Access Control Object and the other LwM2M Objects">
      <figcaption>Illustration of the relations between the LwM2M Access Control Object and the other LwM2M Objects</figcaption>
</figure>

#### LwM2M Access Control Context Switch

In an "Access Control-Disabled" context, the Access Control Object is not instantiated. In that case, adding a new LwM2M Server Account, requires the LwM2M Client to switch from the current "Access Control-Disabled" context to an "Access Control-Enabled" context which means the Access Control Object MUST be instantiated. This context switch must be managed in a Bootstrap Phase.

Note: The "Bootstrap-Discover" operation allows to retrieve data regarding the configuration of the initial "Access Control-Disabled" context (list of Objects, Object Instances and Short Server IDs). The Bootstrap-Server has then all information to setup a proper "Access Control-Enabled" context from the initial context one.

### Authorization


For authorizing an operation to proceed on Object Instance(s) or Resource(s), the LwM2M Client MUST:

1. obtain the access rights for the involved Object Instances:
    * in "Access Control-Disabled" context, full access rights are granted to the LwM2M Server
    * in "Access Control-Enabled" context, access rights MUST be granted to the LwM2M Server according to Section [Obtaining Access Right]()
2. check if that access rights granted to the Server are sufficient for the requested operation according to [Table Authorization]()
3. verify –when the check in 2. on access rights is successful– if the requested operation is supported by the targeted Resource(s) (details are provided in Section [Operation on Resource(s) and Object Instance(s)]() and Section [Operation on Object]()).

The LwM2M Object specification defines which operations are allowed to be performed on Resource within an Object Instance, see supported operations in Section [LwM2M Object Template and Guidelines (Normative)](). The operations allowed on a given Resource MUST apply to all the Resource Instances of that Resource.

<table>
    <caption>Authorization</caption>
    <thead>
        <tr>
            <th>LwM2M Operations</th>
            <th>Minimum Access Right</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>READ – READ-COMPOSITE - OBSERVE – OBSERVE-COMPOSITE - WRITE-ATTRIBUTE</td>
            <td>R</td>
        </tr>
        <tr>
            <td>WRITE - WRITE-COMPOSITE</td>
            <td>W</td>
        </tr>
        <tr>
            <td>DISCOVER</td>
            <td>-</td>
        </tr>
        <tr>
            <td>DELETE</td>
            <td>D</td>
        </tr>
        <tr>
            <td>EXECUTE</td>
            <td>E</td>
        </tr>
    </tbody>
</table>



#### Obtaining Access Right

In "Access Control-Disabled" context, the LwM2M Server get full access rights.


In "Access Control-Enabled" context:
   * for "Create" operation sent by the LwM2M Server, the LwM2M Client MUST get the access right from the ACL Resource Instance corresponding to this LwM2M Server and located in the Access Control Object Instance associated to the targeted Object. Such an Access Control Object Instance – if it exists – has been provisioned during a Bootstrap Phase (Access Control Owner is MAX\_ID=65535). If this access right does not have the "Create" value, or cannot be obtained, the LwM2M Server has no access right.

   * For operations, except the "Create" operation, the LwM2M Client MUST retrieve the Access Control Object Instance associated with the Object Instance the LwM2M Server has requested access to, and MUST proceed according to the sequence below:

     1. If the LwM2M Server is declared as the Access Control Owner of this Object Instance and there is no ACL Resource Instance for that LwM2M Server, then the LwM2M Client gets full access right.

     2. If the LwM2M Client has an ACL Resource Instance for the LwM2M Server, the LwM2M Client gets the access right from that ACL Resource Instance.
     3. If the LwM2M Server is not declared as the Access Control Owner of this Object Instance and the LwM2M Client does not have the ACL Resource Instance for that Server, the LwM2M Client gets the access right from the ACL Resource Instance (ID:0) containing the default access rights if it exists (Section [Access Control on Object Instance]()).
     4. If the LwM2M Client does not have the ACL Resource Instance ID:0 containing the default access rights, then the LwM2M Server has no access rights.
     5. In case of a Composite operation (Read-Composite, Write-Composite, Observe-Composite), the previous four conditions apply to determine the access right for any Object Instance targeted by the Composite Operation. Composite operations have additional characteristics to determine the final access right granted to the LwM2M Server:
       * due to the atomic nature of the Write-Composite operation, all Object Instances involved in that operation MUST have the "Write" access right granted to the requesting LwM2M Server to establish that the "Write" access right is globally granted to such an LwM2M Server for that operation; otherwise, the LwM2M Server has no access right granted.
       * due to the non-atomic nature of the Read-Composite and Observe-Composite operations, any Object Instance involved in the requested operation which has no "Read" access right granted to the requesting LwM2M Server MUST be ignored. If at least one of the Object Instances involved in the requested operation has a "Read" access right granted to the LwM2M Server, the "Read" access right is globally granted to such an LwM2M Server for that operation; otherwise the LwM2M Server has no access right granted.


#### Operation on Resource(s) and Object Instance(s)

When the LwM2M Server targets Resource(s) or Object Instance(s) in a operation, the LwM2M Client MUST obtain an access right for that Server on the Object Instance(s) involved in that operation according to Section [Obtaining Access Right](). The LwM2M Client MUST then check if the access right is granted prior to performing the requested operation. If the operation is not permitted, the LwM2M Client MUST send an "Unauthorized" error code to the LwM2M Server.

If the operation is permitted, for the "Read-Composite" and "Observe-Composite" operations, and for all Object Instances which have not been ignored during the access right determination (see Section [Obtaining Access Right]()), the LwM2M Client MUST retrieve all the requested Resources supporting the "Read" operation and sends such retrieved Resource(s) information to the LwM2M Server.

#### Operation on Object

When the LwM2M Server targets an Object for the "Create" operation, the LwM2M Client MUST obtain an access right for the LwM2M Server of the Object according to Section [Obtaining Access Right]() and MUST check if the access right is granted prior to perform the requested operation.

No access rights are needed for the "Discover" operation on an Object, i.e. the LwM2M Client MUST perform the operation.

For the "Read" and "Observe" operations, the LwM2M Client MUST obtain the access right for the LwM2M Server on each Object Instance according to Section [Obtaining Access Right]() and the LwM2M Client MUST retrieve all the Object Instances for which the LwM2M Server has the "Read" access right. For each of these qualified Object Instances, the LwM2M Client MUST retrieve all Resources except the Resources which do not support the "Read" operation. The LwM2M Client MUST then aggregate the information produced by the operation on each of these Object Instances individually and then send it to the LwM2M Server.

For the "Write-Attributes" operation, the LwM2M Client MUST perform the operation.

#### Notify Operation Consideration

If the LwM2M Client needs to send a "Notify" operation containing an Object Instance or a Resource to the LwM2M Server, the LwM2M Client MUST check if the LwM2M Server is authorized for the "Read" operation. If the LwM2M Server is not authorized, the Client MUST NOT send the "Notify" operation.
