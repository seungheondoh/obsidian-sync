---
tags: [ml, music-llm, experiment]
status: running
experiment: default
started: 2026-04-29 03:06:57
updated: 2026-04-29 03:06:57
best_val_loss: 9.5237
---

# Experiment: default

> Status: **RUNNING** | Started: `2026-04-29 03:06:57` | Updated: `2026-04-29 03:06:57`

## Model Configuration

| Parameter | Value |
|-----------|-------|
| `model_path` | `Qwen/Qwen3-0.6B` |
| `audio_encoder` | `mel_spec` |
| `adapter` | `mlp` |
| `lora_rank` | `128` |
| `precision` | `32` |
| `max_steps` | `1000` |
| `batch_size` | `?` |

## Training Metrics

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|
| 1 | 0 | -1.0000 | 9.5237 | -1.00e+00 |

## Loss Trend (ASCII)

```
val_loss  9.524 | |
                  | |
                  | |
                  | |
                  | |
                  | |
                  | |
          9.524 | |
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