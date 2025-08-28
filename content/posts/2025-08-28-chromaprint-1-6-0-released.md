---
layout: post
title: Chromaprint 1.6.0 released
date: 2025-08-28
categories:
- acoustid
tags:
- acoustid
- chromaprint
- release
---

We've released a new version of Chromaprint with FFmpeg 8.0 support and several performance improvements:

 - Added support for FFmpeg 8.0
 - Added new function `chromaprint_decode_fingerprint_header`
 - Added missing `chromaprint_get_algorithm` function
 - Optimized simhash calculation for better performance
 - Enhanced fingerprint decoding speed
 - Improved fingerprint compression by pre-allocating vector storage
 - Updated CMake minimum version to 3.10 with better build configuration
 - Added Linux ARM64 binary builds
 - Added option to exclude internal avresample

You can download it at [GitHub](https://github.com/acoustid/chromaprint/releases/tag/v1.6.0).