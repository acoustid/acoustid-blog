---
layout: post
title: Chromaprint 1.6.1 released
date: 2026-07-28
categories:
- acoustid
tags:
- acoustid
- chromaprint
- release
---

We've released Chromaprint 1.6.1, a bug-fix release with improved compatibility and audio processing.

 - Fixed a heap buffer overflow when decoding fingerprints with extra data after the encoded values. Applications that decode fingerprints from untrusted sources should update.
 - Restored support for building against FFmpeg 4.x
 - Fixed handling of audio buffers that do not end on a frame boundary
 - Fixed an implicit integer-conversion warning on LLVM
 - Fixed installing to absolute paths
 - Updated CI to build `fpcalc` against the system FFmpeg

You can download it at [GitHub](https://github.com/acoustid/chromaprint/releases/tag/v1.6.1).
