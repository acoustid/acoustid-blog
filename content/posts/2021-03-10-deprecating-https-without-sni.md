---
title: Deprecating HTTPS API access without SNI
date: 2021-03-10
draft: true
tags:
 - acoustid
 - api
 - breaking_change
---

The AcoustID API can be access using either HTTP or HTTPS.
We historically did not require the client to support [SNI](https://en.wikipedia.org/wiki/Server_Name_Indication) for HTTPS.
That means that we need to have dedicated IP addresses for serving HTTPS traffic, which is becoming a problem as the service is growing.

Starting from May 1, 2021, we will drop support for HTTPS traffic without SNI. Requests the right domain name in SNI will be ignored.
If your application is affected by this, you have three options:

1. Upgrade to a HTTPS client that supports SNI. SNI is quite an old protocol now, so it shouldn't be very difficult to find a library for any programming language.
2. If you can't upgrade, you can switch to unencrypted HTTP. This is a temporary measure, as HTTP access will also be deprecated at some point.
3. If you can't upgrade and want to continue using HTTPS, you will need to setup a proxy server for accessing the AcoustID API.
