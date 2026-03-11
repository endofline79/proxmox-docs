# Storage

Snapshot taken on `2026-03-10`.

## Configured storage

| Name | Type | Status | Purpose |
| --- | --- | --- | --- |
| `local` | `dir` | active | templates, ISOs, imports, backups |
| `local-zfs` | `zfspool` | active | VM images and container rootdirs |
| `HDD12tb01` | `zfspool` | active | VM images and container rootdirs |
| `M2EVO1tb` | `zfspool` | active | VM images and container rootdirs |
| `pbs` | `pbs` | inactive | remote backup datastore `backups` |

## Capacity snapshot

- `HDD12tb01`: about `11.58 TiB` total, `3.22%` used
- `M2EVO1tb`: about `0.94 TiB` total, `32.08%` used
- `local`: about `444 GiB` total, `92.85%` used
- `local-zfs`: about `42.98 GiB` total, `26.11%` used

## Observations

- `local` is comparatively full and should be watched.
- `pbs` was unreachable during inventory with `No route to host` to `pbs.occido.net:8007`.
- `pb-server` uses both `M2EVO1tb` and `HDD12tb01`.
