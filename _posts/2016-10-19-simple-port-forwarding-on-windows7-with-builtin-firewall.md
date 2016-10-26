---
layout: post
title: Simple port forwarding on Windows 7 with the builtin firewall
---

Run this in an elevated command prompt:

    netsh interface portproxy add v4tov4 listenport=8080 listenaddress=10.0.0.1 connectport=80 connectaddress=192.168.56.100

Where the "listen" arguments are the "external" side, and the "connect" arguments are the "internal" side.

To remove it:

    netsh interface portproxy delete v4tov4 listenport=8080 listenaddress=10.0.0.1
