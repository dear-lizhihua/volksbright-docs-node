#### Certificate object

<!-- YAML
changes:
  - version:
      - v19.1.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/44935
    description: Add "ca" property.
  - version:
      - v17.2.0
      - v16.14.0
    pr-url: https://github.com/nodejs/node/pull/39809
    description: Add fingerprint512.
  - version: v11.4.0
    pr-url: https://github.com/nodejs/node/pull/24358
    description: Support Elliptic Curve public key info.
-->

A certificate object has properties corresponding to the fields of the
certificate.

* `ca` {boolean} `true` if a Certificate Authority (CA), `false` otherwise.
* `raw` {Buffer} The DER encoded X.509 certificate data.
* `subject` {Object} The certificate subject, described in terms of
  Country (`C`), StateOrProvince (`ST`), Locality (`L`), Organization (`O`),
  OrganizationalUnit (`OU`), and CommonName (`CN`). The CommonName is typically
  a DNS name with TLS certificates. Example:
  `{C: 'UK', ST: 'BC', L: 'Metro', O: 'Node Fans', OU: 'Docs', CN: 'example.com'}`.
* `issuer` {Object} The certificate issuer, described in the same terms as the
  `subject`.
* `valid_from` {string} The date-time the certificate is valid from.
* `valid_to` {string} The date-time the certificate is valid to.
* `serialNumber` {string} The certificate serial number, as a hex string.
  Example: `'B9B0D332A1AA5635'`.
* `fingerprint` {string} The SHA-1 digest of the DER encoded certificate. It is
  returned as a `:` separated hexadecimal string. Example: `'2A:7A:C2:DD:...'`.
* `fingerprint256` {string} The SHA-256 digest of the DER encoded certificate.
  It is returned as a `:` separated hexadecimal string. Example:
  `'2A:7A:C2:DD:...'`.
* `fingerprint512` {string} The SHA-512 digest of the DER encoded certificate.
  It is returned as a `:` separated hexadecimal string. Example:
  `'2A:7A:C2:DD:...'`.
* `ext_key_usage` {Array} (Optional) The extended key usage, a set of OIDs.
* `subjectaltname` {string} (Optional) A string containing concatenated names
  for the subject, an alternative to the `subject` names.
* `infoAccess` {Array} (Optional) An array describing the AuthorityInfoAccess,
  used with OCSP.
* `issuerCertificate` {Object} (Optional) The issuer certificate object. For
  self-signed certificates, this may be a circular reference.

The certificate may contain information about the public key, depending on
the key type.

For RSA keys, the following properties may be defined:

* `bits` {number} The RSA bit size. Example: `1024`.
* `exponent` {string} The RSA exponent, as a string in hexadecimal number
  notation. Example: `'0x010001'`.
* `modulus` {string} The RSA modulus, as a hexadecimal string. Example:
  `'B56CE45CB7...'`.
* `pubkey` {Buffer} The public key.

For EC keys, the following properties may be defined:

* `pubkey` {Buffer} The public key.
* `bits` {number} The key size in bits. Example: `256`.
* `asn1Curve` {string} (Optional) The ASN.1 name of the OID of the elliptic
  curve. Well-known curves are identified by an OID. While it is unusual, it is
  possible that the curve is identified by its mathematical properties, in which
  case it will not have an OID. Example: `'prime256v1'`.
* `nistCurve` {string} (Optional) The NIST name for the elliptic curve, if it
  has one (not all well-known curves have been assigned names by NIST). Example:
  `'P-256'`.

Example certificate:

<!-- eslint-skip -->

```js
{ subject:
   { OU: [ 'Domain Control Validated', 'PositiveSSL Wildcard' ],
     CN: '*.nodejs.org' },
  issuer:
   { C: 'GB',
     ST: 'Greater Manchester',
     L: 'Salford',
     O: 'COMODO CA Limited',
     CN: 'COMODO RSA Domain Validation Secure Server CA' },
  subjectaltname: 'DNS:*.nodejs.org, DNS:nodejs.org',
  infoAccess:
   { 'CA Issuers - URI':
      [ 'http://crt.comodoca.com/COMODORSADomainValidationSecureServerCA.crt' ],
     'OCSP - URI': [ 'http://ocsp.comodoca.com' ] },
  modulus: 'B56CE45CB740B09A13F64AC543B712FF9EE8E4C284B542A1708A27E82A8D151CA178153E12E6DDA15BF70FFD96CB8A88618641BDFCCA03527E665B70D779C8A349A6F88FD4EF6557180BD4C98192872BCFE3AF56E863C09DDD8BC1EC58DF9D94F914F0369102B2870BECFA1348A0838C9C49BD1C20124B442477572347047506B1FCD658A80D0C44BCC16BC5C5496CFE6E4A8428EF654CD3D8972BF6E5BFAD59C93006830B5EB1056BBB38B53D1464FA6E02BFDF2FF66CD949486F0775EC43034EC2602AEFBF1703AD221DAA2A88353C3B6A688EFE8387811F645CEED7B3FE46E1F8B9F59FAD028F349B9BC14211D5830994D055EEA3D547911E07A0ADDEB8A82B9188E58720D95CD478EEC9AF1F17BE8141BE80906F1A339445A7EB5B285F68039B0F294598A7D1C0005FC22B5271B0752F58CCDEF8C8FD856FB7AE21C80B8A2CE983AE94046E53EDE4CB89F42502D31B5360771C01C80155918637490550E3F555E2EE75CC8C636DDE3633CFEDD62E91BF0F7688273694EEEBA20C2FC9F14A2A435517BC1D7373922463409AB603295CEB0BB53787A334C9CA3CA8B30005C5A62FC0715083462E00719A8FA3ED0A9828C3871360A73F8B04A4FC1E71302844E9BB9940B77E745C9D91F226D71AFCAD4B113AAF68D92B24DDB4A2136B55A1CD1ADF39605B63CB639038ED0F4C987689866743A68769CC55847E4A06D6E2E3F1',
  exponent: '0x10001',
  pubkey: <Buffer ... >,
  valid_from: 'Aug 14 00:00:00 2017 GMT',
  valid_to: 'Nov 20 23:59:59 2019 GMT',
  fingerprint: '01:02:59:D9:C3:D2:0D:08:F7:82:4E:44:A4:B4:53:C5:E2:3A:87:4D',
  fingerprint256: '69:AE:1A:6A:D4:3D:C6:C1:1B:EA:C6:23:DE:BA:2A:14:62:62:93:5C:7A:EA:06:41:9B:0B:BC:87:CE:48:4E:02',
  fingerprint512: '19:2B:3E:C3:B3:5B:32:E8:AE:BB:78:97:27:E4:BA:6C:39:C9:92:79:4F:31:46:39:E2:70:E5:5F:89:42:17:C9:E8:64:CA:FF:BB:72:56:73:6E:28:8A:92:7E:A3:2A:15:8B:C2:E0:45:CA:C3:BC:EA:40:52:EC:CA:A2:68:CB:32',
  ext_key_usage: [ '1.3.6.1.5.5.7.3.1', '1.3.6.1.5.5.7.3.2' ],
  serialNumber: '66593D57F20CBC573E433381B5FEC280',
  raw: <Buffer ... > }
```
