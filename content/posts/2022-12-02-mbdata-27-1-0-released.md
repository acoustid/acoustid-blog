---
layout: post
title: mbdata 27.1.0 released
date: 2022-12-02
categories:
- musicbrainz
tags:
- mbdata
- release
---

We've released a new version of the [mbdata](https://github.com/acoustid/mbdata) package. It includes support for the
latest MusicBrainz database schema and also a new command for automatically initializing a database mirror from
scratch.

Setting up a new database mirror can be now as easy as:

    pipx install "mbdata[replication]"

    curl https://raw.githubusercontent.com/acoustid/mbdata/main/mbslave.conf.default -o mbslave.conf
    vim mbslave.conf

    mbslave init --create-user --create-database
    mbslave sync

In addition to the Python package, we also have a container image with the `mbslave` tool at `ghcr.io/acoustid/mbslave:v27.1.0`.
