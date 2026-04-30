---
tags: [ml, music-llm, experiment]
status: running
experiment: adaLN
started: 2026-05-01 00:43:47
updated: 2026-05-01 00:43:47
best_val_loss: 5.8115
---

# Experiment: adaLN

> Status: **RUNNING** | Started: `2026-05-01 00:43:47` | Updated: `2026-05-01 00:43:47`

## Model Configuration

| Parameter | Value |
|-----------|-------|
| `model_path` | `Qwen/Qwen3-0.6B` |
| `audio_encoder` | `mel_spec` |
| `adapter` | `mlp` |
| `conditioning_type` | `adaLN` |
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