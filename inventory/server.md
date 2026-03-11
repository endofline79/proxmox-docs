# Server

- Host: `proxmox`
- IP: `192.168.5.230`
- Role: Proxmox virtualization host
- Access: SSH and API confirmed on 2026-03-10

## Access

- SSH: `ssh proxmox-deneb`
- Web UI: `https://192.168.5.230:8006`
- API: reachable on `https://192.168.5.230:8006/api2/json`
- API token: not stored in this repo

## Platform

- Proxmox release: `9.1`
- Proxmox version: `9.1.1`
- Host OS: `Debian GNU/Linux 13 (trixie)`
- Kernel: `6.17.2-1-pve`
- CPU: `AMD EPYC 7532 32-Core Processor`
- CPU topology: `1 socket / 32 cores / 64 threads`
- RAM: `128 GiB`
- Boot mode: `legacy-bios`
- Hardware vendor: `ASRockRack`
- Hardware model: `ROMED8-2T`

## Current state

- Root filesystem usage on host is low.
- `pbs` storage is configured but currently inactive from this node because `pbs.occido.net:8007` returned `No route to host` during inventory.

## Notes

- Keep credentials and tokens out of git.
