# Storage

Snapshot taken on `2026-03-10`.

## Configured storage

| Name | Type | Status | Purpose |
| --- | --- | --- | --- |
| `local` | `dir` | active | templates, ISOs, imports, backups |
| `local-zfs` | `zfspool` | active | Proxmox-local VM images and container rootdirs |
| `HDD12tb01` | `zfspool` | active | large-capacity data, VM images, container rootdirs |
| `M2EVO1tb` | `zfspool` | active | fast VM and LXC hosting |
| `pbs` | `pbs` | inactive | remote backup datastore `backups` |

## Intent

- `M2EVO1tb` is the fast `1 TB` M.2 drive and is used to host VMs and LXCs.
- `HDD12tb01` is intended for larger data sets, such as Audiobookshelf content and other media.
- `local-zfs` is the Proxmox `500 GB` M.2 storage.
- `pb-server` is the Proxmox Backup Server VM and has a `3 TB` disk on `HDD12tb01`.

## Capacity snapshot

- `HDD12tb01`: about `11.58 TiB` total, `3.22%` used
- `M2EVO1tb`: about `0.94 TiB` total, `32.08%` used
- `local`: about `444 GiB` total, `92.85%` used
- `local-zfs`: about `42.98 GiB` total, `26.11%` used

## Observations

- `local` is comparatively full and should be watched.
- `pbs` was unreachable during inventory with `No route to host` to `pbs.occido.net:8007`.
- `pb-server` uses both `M2EVO1tb` and `HDD12tb01`.
- The Proxmox host currently shows a failed unit for `zfs-import@M2-EVO1TB.service`.
- Storage is currently not in a great place.
- More storage is needed on this server.
- A real backup target is still needed, especially for media and important VMs.
