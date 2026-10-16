---
layout: post
title: Chromaprint 1.6.2 released
date: 2026-10-15
categories:
- acoustid
tags:
- acoustid
- chromaprint
- release
---

We've released Chromaprint 1.6.2, a bug-fix release focused on robustness in `fpcalc` and the fingerprint encoding/decoding API.

 - Fixed a crash in `fpcalc` when the channel layout changes mid-stream (e.g. AC-3 files switching between 5.1 and stereo)
 - Fixed decoding of audio with more than 8 planar channels in `fpcalc`
 - Fingerprint decoding now rejects invalid input that previously caused undefined behaviour
 - The C API encoding/decoding functions now return an error for a negative size, a `NULL` buffer with a nonzero size, and, when encoding, more items than the fingerprint header can hold (previously these were silently truncated)

You can download it at [GitHub](https://github.com/acoustid/chromaprint/releases/tag/v1.6.2).
