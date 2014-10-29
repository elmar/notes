Bonjour / Zeroconf / mDNS
=========================

## IP Addresses

### IPv4

(TODO)

typically DHCP; fall back to APIPA

### IPv6

(TODO)

Link Local Addresses are an integral part of IPv6

### IPv6 only?

Since link local addresses come natural with IPv6 and are rather ad hoc in IPv4
it could be better to just use IPv6 only.  Implications?

## ad hoc DNS

## Service Discovery

TODO

Sleep Proxy Service
-------------------

Part of Bonjour

Allows participating computers to go to sleep and still maintain the presence
of services that they provide.  The sleep proxy server takes over the IP
address of the client when the later goes to sleep and wakes them up when a
request comes along that the client is expected to answer.  All simple tasks
(presence information mainly) is done by the sleep proxy server without waking
the client.

To the network (ARP, IPv6 ND, etc.) it appears as if a device (the sleep proxy
server represented by its MAC address) is stealing the IP address of the
client.

Wide Area Bonjour
-----------------

The [Service Discovery](http://dns-sd.org) part is not only useful with mDNS but can be incorporated into regular DNS.  This is then called _Wide Area Bonjour_.

TODO:
* NAT-PMP
* UPnP
* Back-to-My-Mac

References
----------

* [About Wake on Demand and Bonjour Sleep Proxy](http://support.apple.com/kb/HT3774) (Apple)
* [Stuart Cheshire presenting Bonjour](http://www.youtube.com/watch?v=ZhtZJ6EsCXo) (YouTube)

* [Bonjour Sleep Proxy](https://en.wikipedia.org/wiki/Bonjour_Sleep_Proxy) (Wikipedia)
* [Bonjour Sleep Proxy service stealing IP addresses](https://discussions.apple.com/thread/2160614)

