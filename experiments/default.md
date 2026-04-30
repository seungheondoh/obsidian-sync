---
tags: [ml, music-llm, experiment]
status: running
experiment: default
started: 2026-04-30 22:58:05
updated: 2026-04-30 23:11:38
best_val_loss: 3.4826
---

# Experiment: default

> Status: **RUNNING** | Started: `2026-04-30 22:58:05` | Updated: `2026-04-30 23:11:38`

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
| 1 | 0 | -1.0000 | 9.5222 | -1.00e+00 |
| 2 | 250 | 3.4512 | 3.5214 | 4.53e-05 |
| 3 | 500 | 3.0837 | 3.4826 | 2.51e-05 |

## Loss Trend (ASCII)

```
val_loss  9.522 |█  |
                  |█  |
                  |█  |
                  |█  |
                  |█  |
                  |█  |
                  |█  |
          4.238 |█  |
                   └───┘
                   step 1step 3
train_loss 3.451 | █ |
                   | ██|
                   | ██|
                   | ██|
                   | ██|
                   | ██|
                   | ██|
           -0.444 | ██|
                    └───┘
                    step 1step 3
```

## Generated Captions

### Epoch 1 (step 0)

>  A' means' A Words' Dreams' is A' is, and you can
, and A is the Foxes, and a Grace, Munch M, Ma, Maybe A, a, a, and I, Could, the More Mindset, a, and a, or something, a song, a, or, and, or, and, or, and, a, and a, or, or, or, a, etc, or, and, or, or, the First, or, etc, and, or, or, a, or, or, or, or, and, or,
