# vllm-01 Runbook

Host: `vllm-01`

Purpose: serve one local model at a time on the dedicated GPU.

## Hardware

- GPU: `Radeon AI Pro R9700 R9700 CT 32GB 256-bit GDDR6 PCI Express 5.0 x16`

## Models

- `Qwen/Qwen3-14B` on port `8003`
- `meta-llama/Llama-3.1-8B-Instruct` on port `8002`

## Important rule

Run only one model at a time. The `32 GB` GPU cannot fit both concurrently.

## Start Qwen3-14B

```bash
sudo systemctl start vllm-qwen
sudo journalctl -u vllm-qwen -f
```

## Start Llama-3.1-8B-Instruct

```bash
sudo systemctl start vllm-llama
sudo journalctl -u vllm-llama -f
```

## Switch between models

```bash
sudo systemctl stop vllm-qwen
sudo systemctl start vllm-llama
```

Reverse that pattern if switching back to Qwen.

## Test endpoints

```bash
curl http://localhost:8003/v1/models
curl http://localhost:8002/v1/models
```

Only the endpoint for the currently running model is expected to succeed.
