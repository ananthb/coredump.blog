---
title: "systemd-cri: Containers Without a Container Runtime"
date: 2026-04-05
draft: true
categories:
  - featured
---

[systemd-cri](https://github.com/ananthb/systemd-cri) implements the
Kubernetes Container Runtime Interface (CRI) using only systemd and D-Bus.
No containerd, no CRI-O — just systemd managing pods and containers as
transient units.

Written in Go, it speaks CRI gRPC and uses an embedded SQLite store for state.
The only runtime dependency is systemd itself.
