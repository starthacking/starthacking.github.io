---
layout: page
title: Internet 101
permalink: /web/internet101
categories:
  - web
  - mac
  - windows
  - gnu-linux
hierarchy:
  -
    name: "Topics"
    path: "/topics"
  -
    name: "Web"
    path: "/web"
---

The goal of section is to provide some background on the underlying
infrastructure and technology that makes the Internet work.

Let's dive into exactly what happens from when you type `https://google.com`
in your browser to the moment it shows up on your screen.

## Internet Addressing

When the Internet was first founded it nothing more than a network of
computers for academic purposes. There was no way to go to `google.com`
because there was no concept of a named website, or a **domain**.

Computers were connected to each other solely based on an address of the form
`xxx.xxx.xxx.xxx`, where `xxx` is a number from 0 to 255. This address is
known as an **IP address**, and this is what our computer systems still use.

When you go to a domain it looks up the underlying IP address using the
**Domain Name System** (DNS) and directs you there. For example, Google's
IP address for my region is `216.58.219.46`. Google actually has different
servers for each region to handle demand, so you may see a
different IP.

> Check it out! Open Terminal if you're on a Mac ([instructions][ins-m]), or
> Command Prompt if you're on a PC ([instructions][ins-w]). Type in `ping
> google.com` and see Google's IP address for yourself!

Additionally, IP addresses are unique: no two servers can share the same IP
address. Can you see why non-unique IPs would be a problem?

> More recently, these addresses can also take a form of
> `xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx`, where `x` is a [hexadecimal
> number](https://en.wikipedia.org/wiki/Hexadecimal) between 0 and 15! This
> hexadecimal notation, commonly referred to as
> [IPv6](https://en.wikipedia.org/wiki/IPv6), was developed in 2012 after we
> began running out of simpler IP addresses.

## Domain Name System

What if you had to memorize an IP address for every website you wanted to
visit? Instead of `facebook.com`, you would have to memorize `19.27.5.20`.
It's obvious that remembering `facebook.com` is way easier. This is why the
Domain Name System (DNS) was invented.

DNS functions like the digital equivlant of a yellow telephone book: it lets
your computer look up a **domain name** and find an equivalent
**numerical IP address**. Since the Internet is huge, no one server
can contain the entire database. Instead, DNS is a distributed data store.
This is for safety as well as security: can you imagine if DNS went down, or
someone was able to hack into it?

Many different computers host a small portion of the DNS database and use a
common set of software to communicate. We call these computers **DNS
servers**. Since all of these DNS servers can communicate between one
another, if a DNS server does not contain the domain name requested, it
simply redirects the request to the next server which may contain the desired
information. This way, you're continually redirected down the hierachy until
you get to the domain name you request (as in the figure below).

![Image](https://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper_files/ruswp_diag6.gif)

([Diagram source][dns-diagram-src])
{: .small}

> Check it out! What DNS server are you using? Type in `nslookup
> facebook.com` in either Command Prompt ([Windows][ins-w]), or Terminal
> ([Mac][ins-m]).

## HTTP and the World Wide Web

So what really happens when you type `google.com` into your browser? Once DNS
translates the domain name into an IP address, your request is sent to the
Google server with that IP address. This request is went over the
**HyperText Transfer Protocol** (HTTP). **HyperText** is structured text that
contains connections (links, or URLs) between servers containing text.
Therefore, the HyperText Transfer Protocol specifies how to transfer
hypertext between servers. This is why most URLs are prefixed with
**`http://`**`facebook.com`. When you add the `http://`, you're telling your
web browser to use the HTTP protocol (as opposed to HTTPS, FTP, etc.).

To put this into practice, let's imagine our server requests a particular
file, `silverman.jpg`. Our server could see this request, and will respond
with a **status code** and a message payload. In this case, it will respond
with HTTP `200 OK`, meaning that the request was successful, and a copy of
`silverman.jpg`.

HTTP is a request-response protocol: each response must be triggered by a
corresponding request. It's also **connectionless**: after the request is
serviced, the connection between your web browser and a server is
disconnected. A new connection must be made for each request. This is why web
developers try to minimize **latency**, or the time to initialize a new
connection, by bundling smaller requests for information together into one
larger request.

### Try it out! Simulate an HTTP request on your own

Now that you know how HTTP works, let's simulate how these transactions work.
In this exercise, we'll use `telnet`, a text-communication tool between
servers, to simulate an HTTP request.

> Note: if you're on Windows, you'll have to enable telnet using these
> [instructions](https://kb.ctera.com/article/how-to-open-a-telnet-session-on-windows-7-or-windows-8-os-16.html).
> If you're on a Mac, please follow our [Mac Setup
> Instructions](https://starthacking.org/mac/), then run `brew install
> telnet` in the terminal.

Begin by opening the [Terminal][ins-m] or [Command Prompt][ins-w]. Type
`telnet example.com 80`.

> What does the `80` mean? Each web server runs on a particular port. Think
> of ports like a house number: you may be on a particular street (IP address),
> but the port will tell you which door to knock on. HTTP servers typically
> run on port 80, HTTPS servers typically run on port 443, DNS servers
> typically run on port 53, and email servers run on port 25. This way, you
> can run multiple services from one computer.

```bash
$ telnet example.com 80
Trying 93.184.216.34...
Connected to example.com.
Escape character is '^]'.
```

When the telnet terminal says it's connected, type in `GET / HTTP/1.1`, press
enter, then type `Host: example.com`, then press enter **twice**.

```bash
$ telnet example.com 80
Trying 93.184.216.34...
Connected to example.com.
Escape character is '^]'.
GET / HTTP/1.1
Host: example.com

HTTP/1.1 200 OK
Age: 292907
Cache-Control: max-age=604800
Content-Type: text/html; charset=UTF-8
Date: Wed, 12 Feb 2020 02:03:50 GMT
Etag: "3147526947+ident"
Expires: Wed, 19 Feb 2020 02:03:50 GMT
Last-Modified: Thu, 17 Oct 2019 07:18:26 GMT
Server: ECS (nyb/1D2F)
Vary: Accept-Encoding
X-Cache: HIT
Content-Length: 1256

<!doctype html>
<html>
<head>
    <title>Example Domain</title>
...
```

If you're on a Windows machine you may not see what you're typing, but rest
assured that it is being entered! Congratulations, you just simulated a
simple HTTP (version 1.1) request to a web server for its root page (`/`).
You should see the corresponding HTML response load into your terminal.

## Putting it all together: loading a URL

Congratulations! You've now learned what IP addresses are, how domain names
map to IP addresses using DNS, how websites are loaded using the HTTP
protocol, and you've even simulated an HTTP request on your own. Let's break
down what happens when you load a URL into your web browser. Let's say you
just typed in *[http://google.com](http://google.com)* into your browser's
URL bar.

![Image](https://cdn.tutsplus.com/net/authors/jeremymcpeak/http1-url-structure.png)

A breakdown of a URL into the protocol, host, port, and resource path.
{: .small}

1. If the URL contains a **domain name**, the browser first connects to your
  computer's DNS server and retrieves the corresponding IP address for the web
  server.
1. The web browser connects to the web server and sends an **HTTP request**
  for the particular resource (webpage, image, etc.). It sends this request to
  port 80 unless you specified another port.
1. The web server recieves the request and checks for the desired resource.
  If it exists, the web server sends a status of `HTTP 200` and a copy of the
  resource as text. If the web server cannot locate the resource, it sends an
  `HTTP 404` code, HTTP-lingo for `Page Not Found`.
1. The web browser recieves the HTTP response and closes the connection.
1. The web browser parses the resource and looks for other page elements
  which may need to be requested. Examples of other page elements may be
  images, audio, or programming scripts.
1. For each element needed, the browser makes additional HTTP requests to the server.
1. When the browser has finished loading all resources it displays the
  completed webpage to you!

[ins-m]: https://www.wikihow.com/Open-a-Terminal-Window-in-Mac
[ins-w]: https://www.wikihow.com/Open-the-Command-Prompt-in-Windows
[dns-diagram-src]: https://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm