---
tags: [ml, music-llm, experiment]
status: running
experiment: cross_attn
started: 2026-05-01 00:32:24
updated: 2026-05-01 00:42:43
best_val_loss: 3.5229
---

# Experiment: cross_attn

> Status: **RUNNING** | Started: `2026-05-01 00:32:24` | Updated: `2026-05-01 00:42:43`

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
| 2 | 250 | 3.3238 | 3.5248 | 4.53e-05 |
| 3 | 500 | 3.0119 | 3.5229 | 2.51e-05 |
| 4 | 750 | 2.7153 | 3.5925 | 1.04e-05 |
| 5 | 1000 | 2.3626 | 3.7117 | 1.24e-10 |

## Loss Trend (ASCII)

```
val_loss  5.811 |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
          3.809 |█    |
                   └─────┘
                   step 1step 5
train_loss 3.324 |     |
                   | ██  |
                   | ████|
                   | ████|
                   | ████|
                   | ████|
                   | ████|
           -0.460 | ████|
                    └─────┘
                    step 1step 5
```