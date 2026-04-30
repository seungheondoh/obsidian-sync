---
tags: [ml, music-llm, experiment]
status: running
experiment: cross_attn
started: 2026-05-01 00:32:24
updated: 2026-05-01 00:34:57
best_val_loss: 3.5248
---

# Experiment: cross_attn

> Status: **RUNNING** | Started: `2026-05-01 00:32:24` | Updated: `2026-05-01 00:34:57`

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

## Loss Trend (ASCII)

```
val_loss  5.811 |█ |
                  |█ |
                  |█ |
                  |█ |
                  |█ |
                  |█ |
                  |█ |
          3.811 |█ |
                   └──┘
                   step 1step 2
train_loss 3.324 |  |
                   | █|
                   | █|
                   | █|
                   | █|
                   | █|
                   | █|
           -0.460 | █|
                    └──┘
                    step 1step 2
```