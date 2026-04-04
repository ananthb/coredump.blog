---
title: "Xenomorph: Live-Replace a Linux Rootfs"
date: 2026-04-05
draft: true
categories:
  - featured
---

[Xenomorph](https://github.com/ananthb/xenomorph) replaces a running Linux root
filesystem with a new in-memory rootfs using `pivot_root(2)`. Feed it an OCI
image, a tarball, or a Containerfile and it builds a new root, gracefully stops
services, and pivots — all without a reboot.

Written in Zig, it integrates with systemd's rescue.target and supports
headless operation via Tailscale for remote SSH access. The old root is
preserved at `/mnt/oldroot` for inspection and recovery.
