# Services

Snapshot taken on `2026-03-10`.

## Proxmox host

Key services observed running:

- `pve-cluster`
- `pvedaemon`
- `pveproxy`
- `pvescheduler`
- `pvestatd`
- `pve-firewall`
- `pve-ha-crm`
- `pve-ha-lrm`
- `chrony`
- `postfix`

Failed service observed:

- `zfs-import@M2-EVO1TB.service`

## LXC 101 `litellm`

Environment:

- Ubuntu `24.04 LTS`
- IP: `10.10.10.10/24`
- Purpose: LiteLLM proxy container

Running services observed:

- `litellm.service`
- `postgresql@16-main.service`
- `docker.service`
- `containerd.service`
- `ssh.service`
- `postfix`

Listening ports observed:

- `0.0.0.0:4000` for LiteLLM
- `127.0.0.1:5432` for PostgreSQL
- `*:22` for SSH

Docker containers:

- none running at inventory time

## LXC 102 `certs`

Environment:

- IP: `10.10.10.25/24`
- Purpose: Let's Encrypt / Certbot certificate management

Expected responsibility:

- manage certificates for `occido.net`
- issue and renew wildcard certificates for `*.occido.net`

## LXC 103 `memory`

Environment:

- IP: `10.10.10.30/24`
- Purpose: legacy SQL-backed agent memory experiment

Lifecycle:

- superseded by using git-backed markdown notes
- candidate for deletion when you are ready

## LXC 104 `bookshelf`

Environment:

- IP: `10.10.10.35/24`
- Purpose: Audiobookshelf server
- Project page: <https://www.audiobookshelf.org/>

Current state:

- side project
- currently empty
- planned content import is more than `500` audiobooks

## LXC 106 `tailscale-gw`

Environment:

- IP: `10.10.10.45/24`
- Purpose: Tailscale gateway

Current state:

- Tailscale routing is not fully configured yet
- intended to be used as internal services come online

Policy:

- this environment must not directly expose services to the public internet
- remote access and service exposure should flow through the Tailscale gateway model

## VM 100 `vllm-01`

Environment:

- IPs:
  - LAN: `192.168.5.144/24`
  - DMZ: `10.10.10.15/24`
- Purpose: vLLM model serving host
- GPU: `Radeon AI Pro R9700 R9700 CT 32GB 256-bit GDDR6 PCI Express 5.0 x16`

Model services:

- `meta-llama/Llama-3.1-8B-Instruct` on port `8002`
- `Qwen/Qwen3-14B` on port `8003`

Operational rule:

- only one model should run at a time
- the `32 GB` GPU cannot fit both models concurrently

Control surface:

- `vllm-qwen` systemd service for `Qwen/Qwen3-14B`
- `vllm-llama` systemd service for `meta-llama/Llama-3.1-8B-Instruct`

## VM notes

- `vllm-01` guest agent is available.
- `Aria` is an active experiment around media consumption plus long-running persistent memory.
- Architectural lesson so far: agent systems need tight code paths and a narrow LLM decision window, or a frontier model is often the better default.
- `pb-server` is the Proxmox Backup Server VM.
- `pb-server` currently has a `3 TB` disk on `HDD12tb01`.
- `ttrss` is a Tiny Tiny RSS server tied to the `Aria_rss` article-classification experiment.
- `ttrss` remains useful and that direction may be revisited.
- `ttrss` guest agent is not currently running.
