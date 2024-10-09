# Internet & Web

Computers in isolation has limited capability. When they are _networked_ (i.e. able to transfer data among each other) their capabilities multiply. Most commonly they can share data among each other.

Network is ubiquitous in computers these days. A sound grasp of how the Internet and Web works is important for any software developer.

## Network and the Internet

### Identifying computers in a network

Each computer in a network (aka _hosts_ or _nodes_ in networking terminology) is _uniquely identified_ with its _IP address._

There are two variants of IP address: the traditional and most widely used _IPv4 addresses_ and its upgrade _IPv6 addresses._ For most practical purposes IPv4 addresses suffice.

| Variant | Example
|---------|-------------
| IPv4    | `10.195.66.1`
| IPv6    | `fe80::9f01:3291:9a7f:aa4a%54`

### Finding a computer in a network

Not all hosts (computers) are connected directly to each other in a network; a host usually need to reach another host through a number of other hosts (_hops_ in networking terminology). Requests and responses are conveyed to hosts in a network by finding a _route_ between them.

You can print the route between your host and another with the `tracert` (trace route) command. Here follows an example that lists the hops to reach `google.com`:

```
PS C:\Users\user> tracert google.com

Tracing route to google.com [74.125.68.102]
over a maximum of 30 hops:

  1     1 ms     2 ms     1 ms  192.168.0.1
  2     5 ms     2 ms     4 ms  10.195.66.1
  3     8 ms     4 ms     3 ms  10.20.242.41
  4     9 ms     1 ms     1 ms  100.64.171.53
  5     6 ms     5 ms     5 ms  10.20.105.5
  6     9 ms     9 ms     5 ms  10.10.100.89
  7     7 ms     6 ms     9 ms  10.14.14.45
  8    14 ms     8 ms    10 ms  103.26.244.34.summitgw.net [103.26.244.34]
  9    39 ms    36 ms    36 ms  74.125.32.222
 10    38 ms    39 ms    37 ms  142.251.77.187
 11    36 ms    39 ms    37 ms  142.251.255.56
 12    58 ms    56 ms    56 ms  192.178.242.79
 13    91 ms    87 ms    88 ms  72.14.239.151
 14    89 ms    88 ms    89 ms  142.251.252.45
 15    89 ms    87 ms    88 ms  216.239.35.167
 16     *        *        *     Request timed out.
 17     *        *        *     Request timed out.
 18     *        *        *     Request timed out.
 19     *        *        *     Request timed out.
 20     *        *        *     Request timed out.
 21     *        *        *     Request timed out.
 22     *        *        *     Request timed out.
 23     *        *        *     Request timed out.
 24     *        *        *     Request timed out.
 25    84 ms    85 ms   101 ms  sc-in-f102.1e100.net [74.125.68.102]
```

### DNS servers

A DNS server maps a URL to an IP address.

### Virtual Private Network (VPN)

_To be done._

## The HTTP protocol

Just like any other protocols, HTTP protocol is an agreement across computers on how they communicate with each other.

HTTP is a very widely used protocol and it is very straightforward. An _client_ sends a _request_ to a _server_; the server responds by sending a _response._ Both HTTP requests and responses are chunks of data and comply with a format defined by the HTTP protocol.

Here follows a sample HTTP request:

```
> GET / HTTP/2
> Host: squidfunk.github.io
> user-agent: curl/7.68.0
> accept: */*
>
```

Here follows a sample HTTP response (truncated for brevity):

```
< HTTP/2 404
< server: GitHub.com
< content-type: text/html; charset=utf-8
< permissions-policy: interest-cohort=()
< etag: "66faf066-239b"
< content-security-policy: default-src 'none'; style-src 'unsafe-inline'; img-src data:; connect-src 'self'
< x-github-request-id: 10F5:828B2:2098D6:2375FD:6706D2E2
< accept-ranges: bytes
< age: 0
< date: Wed, 09 Oct 2024 19:00:50 GMT
< via: 1.1 varnish
< x-served-by: cache-qpg1281-QPG
< x-cache: MISS
< x-cache-hits: 0
< x-timer: S1728500451.655837,VS0,VE227
< vary: Accept-Encoding
< x-fastly-request-id: 335b9c29f98a9efccc02baf27f1f85956b479cef
< content-length: 9115
<
<!DOCTYPE html>
<html>
  <head>
```

The most common HTTP client is a web browser. The web pages a browser display are nothing but rendered HTTP responses.

## Web servers or HTTP servers

HTTP servers are _programs_ that can accept HTTP requests and return HTTP responses.
