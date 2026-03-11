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
- `ttrss` is configured with `onboot: 1`.
- `Aria` has a `parent: before_codex` snapshot reference in its VM config.
