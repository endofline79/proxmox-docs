# Networking

Snapshot taken on `2026-03-10`.

## Host interfaces

- `vmbr0`: host bridge with `192.168.5.230/24`
- `vmbr1`: secondary bridge with link-local IPv6 only on the host
- `nic1` is attached to `vmbr0`
- `nic2` is attached to `vmbr1`
- `nic0` is present but down

## Guest placement

- `vmbr0` appears to be the main LAN bridge used by the host and at least some VMs.
- `vmbr1` appears to back the DMZ guest network.
- `litellm`, `certs`, `memory`, `bookshelf`, `tailscale-gw`, `Aria`, and `ttrss` are attached to `vmbr1`.
- `vllm-01` is dual-homed on `vmbr0` and `vmbr1`.
- `pb-server` is attached to `vmbr0`.

## Observations

- The DMZ subnet in use on `vmbr1` is `10.10.10.0/24`.
- `litellm` is at `10.10.10.10`.
- `ttrss` is configured for `10.10.10.40`.
