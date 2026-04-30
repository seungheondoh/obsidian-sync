---
tags: [ml, music-llm, ablation, report]
status: completed
experiment: conditioning_comparison
date: 2026-05-01 04:22:25
steps: 1000
best_method: prefix
best_val_loss: 3.4820
---

# Conditioning Method Comparison — Final Report

> **Generated:** `2026-05-01 04:22:25`  |  **Steps per run:** 1,000  |  **Dataset:** Song Describer

## Research Question

Does the audio conditioning strategy significantly affect music captioning quality when the backbone (Qwen3-0.6B + LoRA + MLP adapter) is held constant?

## Experimental Setup

| Component | Value |
|-----------|-------|
| Base LLM | Qwen/Qwen3-0.6B |
| Audio Encoder | Mel-Spectrogram (128 mel bins, 44.1 kHz, 10 s clips) |
| Adapter | MLP (128 → 1024) |
| LoRA | rank = 128, targets = q/k/v/o_proj |
| Training Steps | 1,000 |
| Optimizer | AdamW (lr=5e-5, β=(0.9, 0.99), fused) |
| Scheduler | Cosine Decay |
| Dataset | Song Describer — train 1,000 / val ~106 |
| Batch Size | 4 |

## Conditioning Methods

| Method | Audio Injection Point | Extra Trainable Params |
|--------|----------------------|------------------------|
| `prefix` | Prepend audio tokens to text token sequence | none |
| `cross_attn` | Per-layer cross-attention (text→audio KV) | CrossAttentionLayer × 28 |
| `adaLN` | Mean-pooled vector modulates each RMSNorm (scale + shift) | AdaLNLayer × 28 |

## Results Summary

| Method | Best Val Loss | Final Val Loss | Final Train Loss | Status |
|--------|-------------|---------------|-----------------|--------|
| `prefix` | **3.4820** ⬅ best | 3.5871 | 2.7460 | completed |
| `cross_attn` | **3.5229** | 3.7117 | 2.3626 | completed |
| `adaLN` | **3.8489** | 4.0143 | 2.6694 | completed |

## Per-Experiment Metrics

### prefix

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|
| 1 | 0 | -1.0000 | 9.5222 | -1.00e+00 |
| 2 | 250 | 3.4460 | 3.5228 | 4.53e-05 |
| 3 | 500 | 3.0834 | 3.4820 | 2.51e-05 |
| 4 | 750 | 2.7915 | 3.5246 | 1.04e-05 |
| 5 | 1000 | 2.7460 | 3.5871 | 1.24e-10 |

### cross_attn

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|
| 1 | 0 | -1.0000 | 5.8115 | -1.00e+00 |
| 2 | 250 | 3.3238 | 3.5248 | 4.53e-05 |
| 3 | 500 | 3.0119 | 3.5229 | 2.51e-05 |
| 4 | 750 | 2.7153 | 3.5925 | 1.04e-05 |
| 5 | 1000 | 2.3626 | 3.7117 | 1.24e-10 |

### adaLN

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|
| 1 | 0 | -1.0000 | 5.8115 | -1.00e+00 |
| 2 | 250 | 4.2793 | 4.3397 | 4.53e-05 |
| 3 | 500 | 3.4373 | 3.8815 | 2.51e-05 |
| 4 | 750 | 2.9717 | 3.8489 | 1.04e-05 |
| 5 | 1000 | 2.6694 | 4.0143 | 1.24e-10 |

## Validation Loss Curves

```
prefix       9.5222 |█    |
                      |█    |
                      |█    |
                      |█    |
                      |█    |
             4.4887 |█    |
                      └─────┘
                       step 1step 5

cross_attn   5.8115 |█    |
                      |█    |
                      |█    |
                      |█    |
                      |█    |
             3.9043 |█    |
                      └─────┘
                       step 1step 5

adaLN        5.8115 |█    |
                      |█    |
                      |█    |
                      |█    |
                      |█    |
             4.1760 |██   |
                      └─────┘
                       step 1step 5

```

## Generated Caption Samples

### prefix

**Step 500:**

> This is a very sad and dark track, with a piano melody and a male vocal.

**Step 750:**

> The song has a melodic and rhythmic feel with the drums, bass and synths. It is a pop song, with the vocals having a male voice. It is a happy and optimistic song.

**Step 1000:**

> A danceable electronic song that can be played in the background of a club.

### cross_attn

**Step 500:**

> A slow, ambient track with a heavy drum beat and a bass sound, with a very organic and natural feel to it, with a male voice and some guitar playing.

**Step 750:**

> A slow piano piece with some string accompaniment, it has a melancholy feel to it.

**Step 1000:**

> Upbeat, fun, and light-hearted Latin American song with a catchy, rhythmic beat and a female singer singing in Spanish.

### adaLN

**Step 500:**

> An upbeat and happy electronic track with a male voice and a simple drum beat.

**Step 750:**

> A slow, melancholic piece of music with a piano, piano and drum machine beat.

**Step 1000:**

> It is an energetic pop song with an acoustic guitar, a male vocal, and drums.

## Analysis

**Winning method at 1,000 steps:** `prefix` (val_loss = 3.4820)

### Method-by-Method Notes

**prefix** — Zero extra parameters beyond the shared adapter + LoRA. The LLM self-attention
must learn to attend selectively to audio tokens interspersed with text tokens. At short
training budgets this is often competitive because there is no extra module to initialise.

**cross_attn** — Adds a full cross-attention layer at every decoder layer. This gives the
model the most expressive temporal alignment between audio frames and generated tokens.
The additional initialisation cost may mean it needs more steps to converge than prefix.

**adaLN** — Uses only a mean-pooled global audio vector; temporal detail is discarded at
the pooling step. The modulation is lightweight and acts on normalisation rather than
attention, making it the lowest-overhead non-trivial conditioning method.

### Caveats

- All results are from only 1,000 training steps — early-stage dynamics may not predict
  final-convergence rankings. Repeat at 10 k–50 k steps for a definitive conclusion.
- The Song Describer validation set is small (~106 samples). Val loss variance may be high.
- Caption quality is assessed qualitatively here. Automatic metrics (METEOR, BERTScore)
  are needed for robust comparison.

## Conclusions

| Method | Complexity | Val Loss | Verdict |
|--------|-----------|----------|---------|
| `prefix` | Low | 3.4820 | **Best at this budget — scale up** |
| `cross_attn` | High | 3.5229 | Competitive — worth scaling |
| `adaLN` | Medium | 3.8489 | Lower priority at this budget |

## Next Steps

- [ ] Scale best method (`prefix`) to 10 k steps
- [ ] Evaluate with METEOR, ROUGE-L, BERTScore on full validation set
- [ ] Ablate LoRA rank (64, 128, 256) with the winning conditioning method
- [ ] Replace Mel-Spec encoder with CLAP for richer semantic features
- [ ] Test prompt variants: genre-specific instructions vs. open-ended captioning

---

## Linked Notes

- [[prefix]]
- [[cross_attn]]
- [[adaLN]]

```dataview
TABLE status, best_val_loss, started
FROM "experiments"
WHERE file.name != "conditioning_comparison_report"
SORT best_val_loss ASC
```
