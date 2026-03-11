# 2026-03-10 Inventory

Initial live inventory was collected over SSH and the Proxmox API.

## Verified access

- SSH access works as `root` via `ssh proxmox-deneb`
- API access works against `https://192.168.5.230:8006`

## Host summary

- Hostname: `proxmox`
- Proxmox version: `9.1.1`
- Kernel: `6.17.2-1-pve`
- CPU: `AMD EPYC 7532 32-Core Processor`
- RAM: `128 GiB`

## Guest summary

- Running VMs: `100 vllm-01`, `204 ttrss`
- Running LXCs: `101 litellm`
- Stopped VMs: `202 Aria`, `203 pb-server`
- Stopped LXCs: `102 certs`, `103 memory`, `104 bookshelf`, `106 tailscale-gw`

## Findings

- Guest ID convention is mostly split by type:
  - LXCs in the `100` range
  - VMs in the `200` range
  - exception: `100 vllm-01` is a legacy VM
- `10.10.10.0/24` is the DMZ network intended for VMs and LXCs.
- `pbs` storage is configured but unreachable from this node at inventory time.
- `local` directory storage is much fuller than the ZFS-backed storage pools.

## Follow-up

- inspect backup connectivity to `pbs.occido.net:8007`
- capture guest purpose and ownership notes
- document bridge intent for `vmbr0` and `vmbr1`
