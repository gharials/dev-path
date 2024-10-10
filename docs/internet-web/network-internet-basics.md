# Networking and Internet Basics

Computers in isolation has limited capability. When they are _networked_ (i.e. able to transfer data among each other) their capabilities multiply. Most commonly they can share data among each other.

Network is ubiquitous in computers these days. A sound grasp of how the Internet and Web works is important for any software developer.

## Network and the Internet

### Identifying computers in a network

Each device connected to a network (e.g. computers, smart phones, routers, cameras, etc.) is _uniquely identified_ with its _IP address._ Devices connected to a network are called _hosts_ or _nodes_ in networking terminology.

There are two variants of IP address: the traditional and most widely used _IPv4 addresses_ and its upgrade _IPv6 addresses._

| Variant | Example
|---------|-------------
| IPv4    | `10.195.66.1`
| IPv6    | `fe80::9f01:3291:9a7f:aa4a%54`

As the preceding example shows, an IPv4 address consists of four parts separated by a dot; each part can have a value up to 255. As the type and number of devices connected to the Internet kept growing, the IPv4 address space got exhausted. IPv6 was introduced as a result to accommodate even more devices. Each device has an IPv6 address as well as its IPv4 address. However, for most practical purposes developers talk in terms of IPv4 addresses.

!!! info
    You can find your computer's IP address by running the `ipconfig` command. Here follows an example:

    ```
    PS C:\Users\user_name> ipconfig
    Windows IP Configuration

    ... ...

    Wireless LAN adapter Wi-Fi:

      Connection-specific DNS Suffix  . :
      IPv4 Address. . . . . . . . . . . : 192.168.0.156
      Subnet Mask . . . . . . . . . . . : 255.255.255.0
      Default Gateway . . . . . . . . . : 192.168.0.1
    ```

### Locating a computer in a network (routing)

In a network not all hosts (computers) are connected directly to each other; a host usually needs to reach another host via a number of intermediate hosts (_hops_ in networking terminology); each intermediate host _relays_ the data sent by the original host. Before exchanging data with another host in a network, the destination host has to be located in the network and a _route_ (consisting of intermediate hosts or hops) has to be found between them; the process is called _routing_.

!!! info
    You can print the route between your host and another with the `tracert` (trace route) command. Here follows an example that lists the hops to reach `google.com`:

    ```
    PS C:\Users\user_name> tracert google.com

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

## Network protocols

Communication between two hosts in a network is a complex process, spanning across several layers. Each layer's operations cannot be arbitrary; they defined by some rules or conventions and they are called _protocols._ The lower layers take care of identifying hosts, finding routes between them, etc. and their corresponding protocols define the rules for them.

!!! info
    The canonical model for the network layers is called the _OSI model_ and it consists of 7 layers. See this resource for further information: [What is the OSI Model? 7 layers explained in detail.](https://www.educative.io/blog/osi-model-layers)

Once the lower layers take care of locating and connecting hosts, then comes the question of _exchanging data_ among the applications or programs running on the hosts. The topmost layer protocols define the rules for communication between applications running on two hosts, thus the layer is called _application layer_. There are many application layer protocols used by various applications. Here follows a few commonly used ones:

| Name           | Purpose    | Applications
|----------------|------------|-------------
| HTTP (Hyper Text Transfer Protocol) | Exchanging hyper texts (web pages.) | HTTP clients (e.g. web browsers) and HTTP servers.
| FTP (File Transfer Protocol)  | Transferring files among computers. | FTP clients and servers.
| SSH (Secured Shell)  | Sending commands to another computer in a network. | Command line interfaces.
| SMTP (Simple Mail Transfer Protocol) | Sending and receiving emails. | Email clients and servers.

So whenever an application (e.g. a web browser) wants to send data to another application (e.g. a web server) in a destination host the following process take place:

1. The application encodes the data according to its protocol rules (e.g. HTTP) and delegate the data to the lower layers.
2. The lower layers locate the destination host, find a route to it, and transfer the data.
3. The target application in the destination receives the data from the lower layers and interprets it.

## The HTTP protocol

Here follows a brief introduction to arguably the most important protocol for developers, that is HTTP protocol. Just like any other protocols, HTTP protocol is an agreement across computers on how they communicate with each other.

HTTP is a very widely used protocol and it is very straightforward. An _client_ sends a _request_ to a _server_; the server responds by sending a _response._ Both HTTP requests and responses are chunks of text that comply with the format defined by the HTTP protocol.

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

See the following resource for a more detailed overview of HTTP: [An overview of HTTP - MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview).

!!! info
    **SMTP protocol message format**

    Just like browsers render HTTP protocol responses in a human readable format, the SMTP clients also do the same for SMTP messages. You can view the SMTP data format by opening an email in your GMail inbox and clicking _Show original_ from the menu at the top-right corner. Here follows an example (truncated for brevity.)

    ```
		Delivered-To: xyz@gmail.com
		Received: by 2002:a05:7301:1295:b0:143:a58e:7c2 with SMTP id li21csp1060487dyb;
				Wed, 9 Oct 2024 07:38:48 -0700 (PDT)
		X-Google-Smtp-Source: AGHT+IF0EsEGjnTjO1OQSvXexSVk0cXsi6tXAtMi9OvnqD4W48BpVZvJ9jhtjZcV/omRJuSVe2ix
		X-Received: by 2002:a05:6808:1918:b0:3e3:9ba3:5ca5 with SMTP id 5614622812f47-3e3e66b83cbmr2574514b6e.4.1728484727789;
				Wed, 09 Oct 2024 07:38:47 -0700 (PDT)
		ARC-Seal: i=1; a=rsa-sha256; t=1728484727; cv=none;
				d=google.com; s=arc-20240605;
				b=V0sGpNclrHonaLsSo0xoUXlEwDcdzbeNvW4EibEwotDLMFSgRwfb0AyK7GL9Nu7v2A
				 oqphKbv6+3WikWFgoIaBvF414W6qEQSNAz7O4lMePge8Jb4dEgjqzlAURXfUtrtsC9tx
				 BazNgxsABLDrbkRx6WXCiXsMJ0vBpGyIOrxeJ9QSv6cQxLQnbdt/RnuqCHfVcqVrymZd
				 8kL693/jYWcNg/PaHnmQOC114OWskO4LghCYsodCNMvVfzs1wMwyaWI3imJoXYyzPwJO
				 f1e//S4RnxNRdNQrYxm6HNcI2A6AQR47JZy5NTF6KfYXP8ny2kon2qO6GTT7851b+lNs
				 qmJQ==
		ARC-Message-Signature: i=1; a=rsa-sha256; c=relaxed/relaxed; d=google.com; s=arc-20240605;
				h=require-recipient-valid-since:feedback-id:list-unsubscribe-post
				 :list-unsubscribe:date:to:mime-version:subject:message-id:from
				 :dkim-signature:dkim-signature;
				bh=4I8kyeWK9z0QNSWoIxvIg13pExRhwI9CyWfOtW5ILnY=;
				fh=CO2obA5JRueXe+/8D0Bn8bvfiXWnfEzdHxRLiyhFm+8=;
				b=kwe2HuwvHGBbJFykARio8/vCB/BUDbs8Ngl7GuD+x9FtCbQWDnVcxLC8nC2kJH4NnO
				 nlRRH0NEANHoIV3TsFd9uGOLWtyWFIBv3dRyzu9RT5MijWzmo9glCx/pNp59UK04ivyg
				 uOhkYC33iAyXQ2TE0KO2y0sigdu5a5Xt3Q4LT92ZhP7cHbDPLPg17Ey3w96K2TOiFSor
				 y98JQTlLs+GaNUVfhAgd3rhCJ5q5A7CG6NaRJ1RTxgNoS/9I/YwA6pbeIMtD6S4kpAvB
				 QbR5bCpmAChkkwEgF6Qo8lyXha8MaKA7m0/w25qzWy9GIhtIBVFHALVXWYBEnEACDcVD
				 EeJw==;
				dara=google.com
		ARC-Authentication-Results: i=1; mx.google.com;
			   dkim=pass header.i=@maile.linkedin.com header.s=d2048-202308-0e header.b=rxdH9Gey;
			   dkim=pass header.i=@linkedin.com header.s=d2048-202308-00 header.b="T1v+/v9R";
			   spf=pass (google.com: domain of m-723o1y6u5nc3q4w91izccdjanxjjmqr07listkcmsu7kfb4qd6losn0mer7@bounce.linkedin.com designates 2620:109:c003:104::202 as permitted sender) smtp.mailfrom=m-723o1y6u5nc3q4w91izccdjanxjjmqr07listkcmsu7kfb4qd6losn0mer7@bounce.linkedin.com;
			   dmarc=pass (p=REJECT sp=REJECT dis=NONE) header.from=linkedin.com
		Return-Path: <m-723o1y6u5nc3q4w91izccdjanxjjmqr07listkcmsu7kfb4qd6losn0mer7@bounce.linkedin.com>
		Received: from maile-db.linkedin.com (maile-db.linkedin.com. [2620:109:c003:104::202])
				by mx.google.com with ESMTPS id 41be03b00d2f7-7e9f6e88b33si10996189a12.776.2024.10.09.07.38.47
				for <xyz@gmail.com>
				(version=TLS1_2 cipher=ECDHE-ECDSA-AES128-GCM-SHA256 bits=128/128);
				Wed, 09 Oct 2024 07:38:47 -0700 (PDT)
		Received-SPF: pass (google.com: domain of m-723o1y6u5nc3q4w91izccdjanxjjmqr07listkcmsu7kfb4qd6losn0mer7@bounce.linkedin.com designates 2620:109:c003:104::202 as permitted sender) client-ip=2620:109:c003:104::202;    
    ```

### HTTP clients

The most common HTTP client is a web browser. The web pages a browser display are nothing but HTTP responses rendered in a human readable format. There are other clients that can issue HTTP requests and receive responses. Two among them are particularly useful for developers: cURL (command line) and [Postman](https://www.postman.com/downloads/) (graphical).

## Web servers or HTTP servers

HTTP servers are _programs_ that can accept HTTP requests and return HTTP responses.
