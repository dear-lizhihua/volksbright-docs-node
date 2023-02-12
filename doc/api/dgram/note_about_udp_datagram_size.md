#### Note about UDP datagram size

The maximum size of an IPv4/v6 datagram depends on the `MTU`
(Maximum Transmission Unit) and on the `Payload Length` field size.

* The `Payload Length` field is 16 bits wide, which means that a normal
  payload cannot exceed 64K octets including the internet header and data
  (65,507 bytes = 65,535 − 8 bytes UDP header − 20 bytes IP header);
  this is generally true for loopback interfaces, but such long datagram
  messages are impractical for most hosts and networks.

* The `MTU` is the largest size a given link layer technology can support for
  datagram messages. For any link, IPv4 mandates a minimum `MTU` of 68
  octets, while the recommended `MTU` for IPv4 is 576 (typically recommended
  as the `MTU` for dial-up type applications), whether they arrive whole or in
  fragments.

  For IPv6, the minimum `MTU` is 1280 octets. However, the mandatory minimum
  fragment reassembly buffer size is 1500 octets. The value of 68 octets is
  very small, since most current link layer technologies, like Ethernet, have a
  minimum `MTU` of 1500.

It is impossible to know in advance the MTU of each link through which
a packet might travel. Sending a datagram greater than the receiver `MTU` will
not work because the packet will get silently dropped without informing the
source that the data did not reach its intended recipient.
