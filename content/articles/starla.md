---
title: "Starla: A RIPE Atlas Probe in Rust"
date: 2026-04-05
draft: true
categories:
  - featured
---

[Starla](https://github.com/ananthb/starla) is a drop-in replacement for the
RIPE Atlas Software Probe, rewritten from scratch in Rust. It connects to the
RIPE Atlas infrastructure and conducts network measurements including Ping,
Traceroute, DNS, HTTP/HTTPS, TLS/SSL, and NTP.

Built on Tokio for async I/O, it uses pure-Rust SSH (russh) for the Atlas
control channel, RocksDB for persistent measurement storage, and optionally
exports Prometheus metrics. Feature flags allow minimal builds for embedded
devices.
