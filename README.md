# frp — Debian Packages

[![Build Debian Packages](https://github.com/line486/frp/actions/workflows/build-deb.yml/badge.svg)](https://github.com/line486/frp/actions/workflows/build-deb.yml)

Automated Debian package builds for [frp](https://github.com/fatedier/frp), a fast reverse proxy to expose a local server behind a NAT or firewall to the internet.

## What this repo does

This is a fork of [fatedier/frp](https://github.com/fatedier/frp) with one addition: a GitHub Actions workflow that automatically builds `.deb` packages for **frpc** and **frps**.

- Checks [upstream releases](https://github.com/fatedier/frp/releases) daily
- When a new upstream release is detected, builds debs and publishes a matching release here
- Also builds on any release published in this repo, or manually via workflow dispatch

## Supported architectures

| Architecture | `.deb` name                                             |
| ------------ | ------------------------------------------------------- |
| amd64        | `frpc_<version>_amd64.deb` / `frps_<version>_amd64.deb` |
| arm64        | `frpc_<version>_arm64.deb` / `frps_<version>_arm64.deb` |
| armhf        | `frpc_<version>_armhf.deb` / `frps_<version>_armhf.deb` |
| i386         | `frpc_<version>_i386.deb` / `frps_<version>_i386.deb`   |

## Install

Download the latest `.deb` from the [releases page](https://github.com/line486/frp/releases) and install:

```bash
sudo dpkg -i frpc_*.deb frps_*.deb
```

Or install only the client or server:

```bash
sudo dpkg -i frpc_<version>_<arch>.deb   # client only
sudo dpkg -i frps_<version>_<arch>.deb   # server only
```

The packages ship with systemd service files — enable and start:

```bash
sudo systemctl enable --now frpc   # or frps
```

Configuration files live at `/etc/frp/frpc.toml` and `/etc/frp/frps.toml`.

## Upstream

For documentation, configuration guides, and the full frp feature set, see the [upstream project](https://github.com/fatedier/frp).
