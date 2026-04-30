---
tags: [ml, music-llm, experiment]
status: running
experiment: adaLN
started: 2026-05-01 00:43:47
updated: 2026-05-01 00:51:33
best_val_loss: 3.8489
---

# Experiment: adaLN

> Status: **RUNNING** | Started: `2026-05-01 00:43:47` | Updated: `2026-05-01 00:51:33`

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
| 2 | 250 | 4.2793 | 4.3397 | 4.53e-05 |
| 3 | 500 | 3.4373 | 3.8815 | 2.51e-05 |
| 4 | 750 | 2.9717 | 3.8489 | 1.04e-05 |
| 5 | 1000 | 2.6694 | 4.0143 | 1.24e-10 |

## Loss Trend (ASCII)

```
val_loss  5.811 |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
                  |██   |
          4.094 |██   |
                   └─────┘
                   step 1step 5
train_loss 4.279 | █   |
                   | █   |
                   | ███ |
                   | ████|
                   | ████|
                   | ████|
                   | ████|
           -0.340 | ████|
                    └─────┘
                    step 1step 5
```