# Training lifecycle checklist

## Data
Verify rights; record source/version/license; document preprocessing; deduplicate exact and near duplicates; split and audit train/validation overlap.

## Tokenizer
Train/select using training data only; record vocabulary, special tokens, normalization and revision; test round-trip; measure sequence length by slice.

## Model
Document architecture and parameter count; test causal masking and autoregressive behavior; record initialization and config.

## Optimization
Define next-token cross-entropy objective; configure optimizer, schedule, warm-up, clipping, accumulation and precision; log train/validation loss, gradient norms, throughput and memory.

## Checkpoint
Save model, optimizer, scheduler, scaler, step, RNG states, data position, config, tokenizer and dataset references, and code revision. Test resume.

## Evaluation and serving
Use held-out data; document tokenizer-aware perplexity; add task probes and error analysis; load weights/tokenizer/config coherently; smoke-test generation and measure latency/memory.