---
title: "nomad-driver-cri: CRI Runtimes for Nomad"
date: 2026-04-05
draft: true
---

[nomad-driver-cri](https://github.com/ananthb/nomad-driver-cri) is a HashiCorp
Nomad task driver plugin that orchestrates containers through any CRI-compatible
runtime — containerd, CRI-O, or anything else that speaks the Kubernetes
Container Runtime Interface.

Written in Go, it bridges Nomad's plugin framework with the CRI gRPC API,
letting Nomad schedule containers on standard Kubernetes runtimes via a Unix
socket.
