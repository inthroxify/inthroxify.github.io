---
layout: post
title: Making Ubuntu Server 14.04 Have a Getty Login on the Console
---

Installed a fresh Trusty VM on XenServer 6.2, but the console in XenCenter only had boot messages, no login. Google searches reveal tips about kernel options, but those are only tangentially related red-herrings.

Create `/etc/init/hvc0.conf` and put this in it:

```
# console - getty
#
# This service maintains a getty on console from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -L hvc0 -8 38400 linux
```

Reboot, or maybe `kill -1 1` will work for you.

Read more:

* [Xen Common Problems](https://wiki.xenproject.org/wiki/Xen_Common_Problems#Console_of_my_PV_guest_shows_kernel_boot_messages_and_then_it_stops_and_doesn.27t_work_anymore) \([Permalink](http://archive.is/zNHJw)\)
* [Background info on hvc0](http://www-archive.xenproject.org/files/xensummit_4/xensummit_linux_console_slides.pdf) \([Permalink](http://archive.is/3Upf0)\)

See also:

* [Install Ubuntu 14.04 on XenServer](https://unyield.com/server-management/installing-ubuntu-14-04-on-xenserver-6-5-via-url-install-guide/) \([Permalink](http://archive.is/RHcb2)\)
