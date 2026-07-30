---
layout: post
title: "Reviving K6's StatsD Extension for Datadog Observability"
date: 2026-07-30 11:00:00 +0000
tags: [tech, devops, sre, observability, k6, datadog, docker]
---

A lot gets said about how data can help us with observability, but much less gets said about how much we can shape the collection itself to actually help us make decisions.

<!--more-->

A few months ago, here at Appoena, I ran into exactly that kind of challenge: a client's team needed to closely track the metrics from their K6 load tests in Datadog, alongside the rest of their observability stack.

## The problem

Unfortunately, K6 v0.55.0 dropped support for sending metrics via StatsD, which happens to be Datadog's recommended way of receiving them. We looked into other ways of getting K6 metrics into Datadog, but every alternative came with trade-offs, including the absence of some extremely important p95 metrics.

## Digging into the docs

While going through K6's documentation, I found a path forward: it's possible to build a custom K6 binary and re-enable the StatsD extension through [xk6](https://github.com/grafana/xk6). So that's exactly what I did.

I put together a custom `Dockerfile`, and after a few failed builds, I landed on a version that worked end to end, sending every metric to the local Datadog Agent and having it show up correctly in the platform.

## Sharing the knowledge

For the client, I handed over everything: the full explanation of the problem and the original `Dockerfile`, so their team could build the image themselves and keep it internalized within their corporate environment.

For the wider DevOps and SRE community, I made the image public. It's been 10 months since the first tag was released, and it has already crossed 2k pulls. Early last month I updated it to the latest K6 version, and I plan to keep this image up to date going forward.

You can find it here: [osnijunior/k6-statsd on Docker Hub](https://hub.docker.com/r/osnijunior/k6-statsd)

This was first posted on my [LinkedIn](https://www.linkedin.com/feed/update/urn:li:activity:7484290058070634497/) - Follow me there!
