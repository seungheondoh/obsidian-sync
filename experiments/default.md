---
tags: [ml, music-llm, experiment]
status: failed
experiment: default
started: 
updated: 2026-04-29 03:05:50
best_val_loss: N/A
---

# Experiment: default

> Status: **FAILED** | Started: `` | Updated: `2026-04-29 03:05:50`

## Model Configuration

| Parameter | Value |
|-----------|-------|

## Training Metrics

| Epoch | Step | Train Loss | Val Loss | LR |
|-------|------|-----------|---------|-----|

## Error

```
Caught ModuleNotFoundError in DataLoader worker process 0.
Original Traceback (most recent call last):
  File "/root/miniconda3/lib/python3.13/site-packages/torch/utils/data/_utils/worker.py", line 349, in _worker_loop
    data = fetcher.fetch(index)  # type: ignore[possibly-undefined]
  File "/root/miniconda3/lib/python3.13/site-packages/torch/utils/data/_utils/fetch.py", line 52, in fetch
    data = [self.dataset[idx] for idx in possibly_batched_index]
            ~~~~~~~~~~~~^^^^^
  File "/workspace/music-llm-claude-lightning-slack-obsidian/mllm/models/data/pt_dataset.py", line 82, in __getitem__
    audio, sr = load_audio(os.path.join(self.data_dir, "audio", row["audio_path"]))
                ~~~~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/workspace/music-llm-claude-lightning-slack-obsidian/mllm/common_utils/audio_utils/audio_io.py", line 31, in load_audio
    y = librosa.resample(y, orig_sr=sr, target_sr=target_sr, res_type='kaiser_fast')
  File "/roo
```