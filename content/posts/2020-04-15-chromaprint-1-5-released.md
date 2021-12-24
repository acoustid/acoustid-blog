---
layout: post
title: Chromaprint 1.5 released
date: 2020-04-15
categories:
- acoustid
tags:
- acoustid
- chromaprint
- release
---

We've released a new version of Chromaprint with a few small changes:

 - Added support for fpcalc -raw -signed, which helps with easier PostgreSQL integration
 - Added support for using libavresample instead of libswresample
 - Fixed possible crash in `chromaprint_decode_fingerprint`
 - Fixed unit tests on big endian CPUs

You can download it at [GitHub](https://github.com/acoustid/chromaprint/releases/tag/v1.5.0).
