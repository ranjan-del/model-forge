# Architecture — Model Forge

## Lifecycle graph
```text
Dataset sources
 -> ingestion manifest
 -> cleaning / dedup / split / leakage audit
 -> tokenizer training or selection
 -> model configuration
 -> training loop + validation
 -> full-state checkpoints
 -> evaluation suite
 -> versioned model artifact + model card
 -> local serving adapter
```

## Proposed package layout
- `data/`: manifests, loaders, preprocessing, deduplication and split checks.
- `tokenization/`: tokenizer adapters, training/inspection utilities.
- `models/`: small decoder-only Transformer modules and config validation.
- `training/`: optimizer, scheduler, mixed precision, gradient accumulation, logging.
- `checkpointing/`: model, optimizer, scheduler, scaler, RNG, step, config, tokenizer references.
- `evaluation/`: loss/perplexity and task-specific evaluators.
- `artifacts/`: metadata schemas and model cards.
- `serving/`: local generation API and compatibility checks.
- `experiments/`: immutable run manifests and comparison reports.

## Checkpoint contract
A resumable checkpoint should include model weights, optimizer state, scheduler state, mixed-precision scaler when used, global step, epoch/data position where meaningful, RNG states, model config, tokenizer reference/hash, dataset manifest hash, and code revision. Recovery tests should compare uninterrupted training with interrupted-and-resumed training within expected numerical tolerance.

## Artifact compatibility
Serving must validate tokenizer and model config hashes. Generation settings should be versioned separately from weights. Missing or mismatched metadata should produce warnings or hard failures according to severity.

## Resource strategy
Begin with CPU/small GPU-compatible configs and tiny datasets. Make sequence length, batch size, gradient accumulation, precision, and checkpoint frequency configurable. Record peak memory and tokens/sec. Do not optimize before profiling.
