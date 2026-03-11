# Conventions

## Guest IDs

- Standard expectation: LXCs use `100`-series IDs.
- Standard expectation: VMs use `200`-series IDs.
- Known exception: VM `100` is the legacy guest `vllm-01`.

## Networks

- `10.10.10.0/24` is the DMZ network for VMs and LXCs.

## Domains and certificates

- `occido.net` is an owned domain.
- LXC `102` (`certs`) is intended to manage Let's Encrypt / Certbot material for `occido.net`.
- Wildcard certificate coverage should include `*.occido.net`.

## Retired directions

- LXC `103` (`memory`) reflects a legacy SQL-backed memory approach.
- Current preference is to keep durable agent/project memory in git-backed markdown repositories when practical.

## Agent design lesson

- Broad, loosely constrained agent behavior is usually a bad trade unless there is a strong reason to keep the model in the loop.
- Favor tight coding and a very specific LLM decision window.
- Otherwise, it is often better to just use a frontier model directly.

## Experiment lineage

- `Aria_rss` used `ttrss` as an article source for preference feedback and article classification experiments.
- That direction is still considered useful and may be tried again with a tighter decision loop.

## Side projects

- LXC `104` (`bookshelf`) is an Audiobookshelf side project.
- It is not yet populated, but there is a substantial planned import of more than `500` audiobooks.

## Exposure policy

- This environment is prohibited from directly hosting services on the public internet.
- LXC `106` (`tailscale-gw`) is the intended access pattern as services come online.
- Tailscale routing is not fully configured yet, so this remains a follow-up item.

## Storage stance

- `M2EVO1tb` is the fast VM/LXC storage tier.
- `HDD12tb01` is the bulk-data tier for media and other large datasets.
- `local-zfs` is the Proxmox-local `500 GB` M.2 storage.
- Storage is currently constrained and needs expansion.
- A stronger backup target is still needed for media and important VMs.

## Repository discipline

- Store sanitized infrastructure notes only.
- Do not commit API tokens, SSH private keys, passwords, or copied auth headers.
- Prefer summary notes over raw command dumps unless the dump is needed for troubleshooting.
