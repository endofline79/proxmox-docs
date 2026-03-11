# Conventions

## Guest IDs

- Standard expectation: LXCs use `100`-series IDs.
- Standard expectation: VMs use `200`-series IDs.
- Known exception: VM `100` is the legacy guest `vllm-01`.

## Networks

- `10.10.10.0/24` is the DMZ network for VMs and LXCs.

## Repository discipline

- Store sanitized infrastructure notes only.
- Do not commit API tokens, SSH private keys, passwords, or copied auth headers.
- Prefer summary notes over raw command dumps unless the dump is needed for troubleshooting.
