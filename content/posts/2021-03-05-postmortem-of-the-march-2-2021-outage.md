---
title: "Postmortem of the March 2, 2021 outage"
date: 2021-03-05T15:38:18+01:00
tags:
 - acoustid
 - outage
 - postmortem
---

On March 2, 2021, we had a large incident that led to the entire acoustid.org infrastructure going down.
This will be the first of at least a few posts to explain what happened, how we got to this situation and
what will happen in the future?

I'll not sugar-coat it, the most direct cause of the problem was the modern equivalent of the classic `rm -rf /` as `root`.
With the classic one, you can only delete data from one server. In the world of Kubernetes, you can delete everything from
all servers at once, and that's exactly what happened.

As part of working on the outgoing performance problems with the API, I was setting up a new Kubernetes cluster to re-route
some read-only traffic from the main Kubernetes cluster. I was testing a new method to bootstrap a stand-by
PostgreSQL cluster from our WAL-G backups. The goal was to have a completely separate environment, that is running without
talking to the master. I needed to delete everything to re-test the bootstrap procedure from scratch after doing
the final changes and I ran `kubectl delete ns acoustid` with `KUBECONFIG` pointing to the wrong config file.

I have full backups of the databases and anyway, the command did not delete the PVs storing the actual data, but it was still
a very bad situation because I did not have backups of the Kubernetes manifests. I had various repositories for
setting things up, but none of them covered the complete environment from scratch.

So I had to collect all the bits and pieces and rebuild everything. The result of this work will become open source in a few days.

AcoustID is now back up, but still not in ideal condition as we were having major performance problems
for the last few months, which are unfortunately no longer solvable just by adding more servers.
Some major changes need to happen, but I'll talk more about that in the next post.

After ten years of existence, this was the worst outage we ever had. I was initially expecting it to be much worse
because the database restoration process was not well tested. I expected it to take weeks to recover everything.
I expected AcoustID to be done after losing most of the customers. It turned out all working fine and I just needed a few days
to put all the small bits together.

I learned a lot from this, and the amazing response I got from people motivates me to keep moving AcoustID forward.

We are still running on the design I did back in 2010. It scaled beyond my imagination. Sure, the infrastructure evolved
a lot, but the software is more or less the same. Over the last weeks, I'll keep posting blog posts about what needs to change.
Some changes will be internal, some will affect the public APIs. 2021 will the year of change for AcoustID.

Thank you for using and supporting AcoustID.
