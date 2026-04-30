---
tags: [ml, music-llm, experiment]
status: running
experiment: cross_attn
started: 2026-05-01 00:32:24
updated: 2026-05-01 00:32:24
best_val_loss: 5.8115
---

# Experiment: cross_attn

> Status: **RUNNING** | Started: `2026-05-01 00:32:24` | Updated: `2026-05-01 00:32:24`

## Model Configuration

| Parameter | Value |
|-----------|-------|
| `model_path` | `Qwen/Qwen3-0.6B` |
| `audio_encoder` | `mel_spec` |
| `adapter` | `mlp` |
| `conditioning_type` | `cross_attn` |
| `lora_rank` | `128` |
| `precision` | `32` |
| `max_steps` | `1000` |
| `batch_size` | `?` |

## Training Metrics

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|
| 1 | 0 | -1.0000 | 5.8115 | -1.00e+00 |

## Loss Trend (ASCII)

```
val_loss  5.812 | |
                  | |
                  | |
                  | |
                  | |
                  | |
                  | |
          5.812 | |
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