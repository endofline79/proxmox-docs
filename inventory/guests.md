# Guests

Snapshot taken on `2026-03-10`.

## ID conventions

- LXC containers normally use IDs in the `100` range.
- VMs normally use IDs in the `200` range.
- Legacy exception: VM `100` is `vllm-01`.

## QEMU VMs

| ID | Name | Status | CPU | Memory | Primary Disk | Network |
| --- | --- | --- | --- | --- | --- | --- |
| 100 | `vllm-01` | running | 16 vCPU | 64 GiB | `M2EVO1tb` 200G | `vmbr0`, `vmbr1` |
| 202 | `Aria` | stopped | 8 vCPU | 8 GiB | `local-zfs` 60G | `vmbr1` |
| 203 | `pb-server` | stopped | 5 vCPU | 4 GiB | `M2EVO1tb` 60G + `HDD12tb01` 2000G | `vmbr0` |
| 204 | `ttrss` | running | 2 vCPU | 2 GiB | `M2EVO1tb` 23.5G | `vmbr1` |

## LXC containers

| ID | Name | Status | CPU | Memory | Rootfs | Network |
| --- | --- | --- | --- | --- | --- | --- |
| 101 | `litellm` | running | 2 vCPU | 2 GiB | `local-zfs` 8G | `vmbr1`, `10.10.10.10/24` |
| 102 | `certs` | stopped | 1 vCPU | 512 MiB | `local-zfs` 4G | `vmbr1`, `10.10.10.25/24` |
| 103 | `memory` | stopped | 1 vCPU | 512 MiB | `local-zfs` 4G | `vmbr1`, `10.10.10.30/24` |
| 104 | `bookshelf` | stopped | 2 vCPU | 1 GiB | `HDD12tb01` 100G | `vmbr1`, `10.10.10.35/24` |
| 106 | `tailscale-gw` | stopped | 1 vCPU | 512 MiB | `M2EVO1tb` 4G | `vmbr1`, `10.10.10.45/24` |

## Notes

- `vllm-01` is the only VM currently using a `100`-series ID.
- `vllm-01` runs the vLLM server workload.
- `vllm-01` owns the GPU: `Radeon AI Pro R9700 R9700 CT 32GB 256-bit GDDR6 PCI Express 5.0 x16`.
- `vllm-01` guest agent is responding and currently reports:
  - `192.168.5.144/24` on the LAN side
  - `10.10.10.15/24` on the DMZ side
- `Aria` is another iteration of Aria focused on media consumption and long-running persistent memory.
- `Aria` is still experimental and not considered dead yet.
- Current lesson from the experiment: agents need tight coding and a very specific decision window for the LLM; otherwise it is often better to just run a frontier model.
- `pb-server` is the Proxmox Backup Server VM.
- `pb-server` has a `3 TB` disk on `HDD12tb01`.
- `certs` is the Let's Encrypt / Certbot container for `occido.net`.
- `certs` should issue and manage wildcard certificates for `*.occido.net`.
- `memory` is a legacy attempt at using SQL as an agent memory repository.
- `memory` is no longer the intended direction and should be deleted at some point.
- `bookshelf` is an Audiobookshelf server: <https://www.audiobookshelf.org/>.
- `bookshelf` is a side project and is currently empty.
- There is a pending backlog to upload more than `500` audiobooks into `bookshelf`.
- `tailscale-gw` is the Tailscale gateway container.
- Tailscale routing is not fully set up yet, but this container should be used as services come online.
- This environment must never directly host services on the public internet.
- `ttrss` is a Tiny Tiny RSS server.
- `ttrss` supported the `Aria_rss` experiment, where Aria was trying to classify articles based on your feedback and make decisions about what you might like.
- `ttrss` is still useful and that experiment direction may be revisited.
- `ttrss` is configured with `onboot: 1`.
- `ttrss` does not currently have a working QEMU guest agent.
- `Aria` has a `parent: before_codex` snapshot reference in its VM config.
