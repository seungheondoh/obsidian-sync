---
tags: [ml, music-llm, experiment]
status: completed
experiment: default
started: 2026-05-01 00:04:31
updated: 2026-05-01 00:31:46
best_val_loss: 3.4820
---

# Experiment: default

> Status: **COMPLETED** | Started: `2026-05-01 00:04:31` | Updated: `2026-05-01 00:31:46`

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
| 2 | 250 | 3.4460 | 3.5228 | 4.53e-05 |
| 3 | 500 | 3.0834 | 3.4820 | 2.51e-05 |
| 4 | 750 | 2.7915 | 3.5246 | 1.04e-05 |
| 5 | 1000 | 2.7460 | 3.5871 | 1.24e-10 |

## Loss Trend (ASCII)

```
val_loss  9.522 |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
                  |█    |
          4.237 |█    |
                   └─────┘
                   step 1step 5
train_loss 3.446 | █   |
                   | ██  |
                   | ████|
                   | ████|
                   | ████|
                   | ████|
                   | ████|
           -0.444 | ████|
                    └─────┘
                    step 1step 5
```