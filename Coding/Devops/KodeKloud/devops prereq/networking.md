## DNS resolution
- check `/etc/hosts` file, if not found 
- check `/etc/resolv.conf` for isp or public dns

_/etc/hosts_
```
127.0.0.1 localhost
```

_/etc/resolve.conf_
```
nameserver 2001:b000:168::2
nameserver 2001:b000:168::1
nameserver 192.168.1.1
```
## records

### A record
- example.com 192.16.1.1 (ipv4)
### AAAA record
- example.com  2001:db8:3333:4444:5555:6666:1.2.3.4 (ipv6)
### CNAME record
- example2.com example.com (another domain name)
## _ping_ vs _nslookup_ vs _dig_

|**Tool**|**Purpose**|**Key Functionality**|**Protocol Used**|
|---|---|---|---|
|**Ping**|Checks network connectivity and measures latency.|Sends ICMP echo requests to a host to test if it is reachable and measures round-trip time.|ICMP (Internet Control Message Protocol)|
|**nslookup**|Queries DNS servers to resolve domain names or IP addresses.|Looks up DNS records (e.g., A, MX, CNAME) and provides information about domain resolution.|DNS (Domain Name System)|
|**dig**|A more advanced DNS query tool for detailed DNS information.|Provides detailed DNS record information, including TTL, authoritative servers, and more.|DNS (Domain Name System)|

## anatomy of a url

`www.google.com`

- **.com**: Top-level domain (TLD)
- **google**: Domain name (second-level domain)
- **www**: Subdomain

The full structure is: `subdomain.domain.tld`.