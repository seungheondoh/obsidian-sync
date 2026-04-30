---
tags: [ml, music-llm, experiment]
status: running
experiment: default
started: 2026-05-01 00:04:31
updated: 2026-05-01 00:04:31
best_val_loss: 9.5222
---

# Experiment: default

> Status: **RUNNING** | Started: `2026-05-01 00:04:31` | Updated: `2026-05-01 00:04:31`

## Model Configuration

| Parameter | Value |
|-----------|-------|
| `model_path` | `Qwen/Qwen3-0.6B` |
| `audio_encoder` | `mel_spec` |
| `adapter` | `mlp` |
| `conditioning_type` | `prefix` |
| `lora_rank` | `128` |
| `precision` | `32` |
| `max_steps` | `1000` |
| `batch_size` | `?` |

## Training Metrics

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|
| 1 | 0 | -1.0000 | 9.5222 | -1.00e+00 |

## Loss Trend (ASCII)

```
val_loss  9.522 | |
                  | |
                  | |
                  | |
                  | |
                  | |
                  | |
          9.522 | |
                   └─┘
                   step 1step 1
train_loss -1.000 | |
                   | |
                   | |
                   | |
                   | |
                   | |
                   | |
           -1.000 | |
                    └─┘
                    step 1step 1
```