---
layout: post
title: Getting the Dell Service Tag from the BIOS via Windows Command Prompt
---

Had a Dell laptop with the physical service tag worn off but needed the service tag to get drivers, etc. Apparently Windows Management Instrumentation can be used to get this out of the bios. Run this at a cmd.exe prompt:

`wmic bios get serialnumber`

Returns output like:

```
SerialNumber
0ABCDE9
```
