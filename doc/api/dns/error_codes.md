## Error codes

Each DNS query can return one of the following error codes:

* `dns.NODATA`: DNS server returned an answer with no data.
* `dns.FORMERR`: DNS server claims query was misformatted.
* `dns.SERVFAIL`: DNS server returned general failure.
* `dns.NOTFOUND`: Domain name not found.
* `dns.NOTIMP`: DNS server does not implement the requested operation.
* `dns.REFUSED`: DNS server refused query.
* `dns.BADQUERY`: Misformatted DNS query.
* `dns.BADNAME`: Misformatted host name.
* `dns.BADFAMILY`: Unsupported address family.
* `dns.BADRESP`: Misformatted DNS reply.
* `dns.CONNREFUSED`: Could not contact DNS servers.
* `dns.TIMEOUT`: Timeout while contacting DNS servers.
* `dns.EOF`: End of file.
* `dns.FILE`: Error reading file.
* `dns.NOMEM`: Out of memory.
* `dns.DESTRUCTION`: Channel is being destroyed.
* `dns.BADSTR`: Misformatted string.
* `dns.BADFLAGS`: Illegal flags specified.
* `dns.NONAME`: Given host name is not numeric.
* `dns.BADHINTS`: Illegal hints flags specified.
* `dns.NOTINITIALIZED`: c-ares library initialization not yet performed.
* `dns.LOADIPHLPAPI`: Error loading `iphlpapi.dll`.
* `dns.ADDRGETNETWORKPARAMS`: Could not find `GetNetworkParams` function.
* `dns.CANCELLED`: DNS query cancelled.

The `dnsPromises` API also exports the above error codes, e.g., `dnsPromises.NODATA`.
