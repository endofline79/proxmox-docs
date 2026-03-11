# Proxmox Notes

Personal operations repository for the Proxmox server at `192.168.5.230`.

This repo is markdown-first on purpose. It is the working memory, runbook, and change log for this machine.

## Layout

- `inventory/`: machine facts and durable reference notes
- `memories/`: longer-lived operational memory and lessons learned
- `runbooks/`: repeatable procedures
- `sessions/`: dated work logs
- `changes/`: notable changes and decisions

## Rules

- Do not commit secrets, tokens, private keys, or raw credential exports.
- Prefer short factual notes over long unstructured dumps.
- Record what changed, why it changed, and how it was verified.
- Keep one topic per file when possible.
