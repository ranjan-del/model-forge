# Model Forge

**A transparent, end-to-end laboratory for training, evaluating, checkpointing, and serving small language models.**

Model Forge aims to teach and demonstrate the full model lifecycle with engineering discipline: data preparation, tokenizer choice, model definition, training, validation, checkpoint recovery, evaluation, and inference. It is not intended to be a copy of a tutorial repository or a claim to train a frontier model.

## Why this project
Many learning projects stop at a training loop. Real model development also requires data provenance, deduplication, leakage control, reproducible configs, validation, checkpoint integrity, evaluation, artifact versioning, and serving. Model Forge makes those lifecycle stages explicit and measurable.

## Proposed differentiator
A **reproducible lifecycle workbench** that links every model artifact to its dataset snapshot, tokenizer, configuration, code revision, training history, evaluation suite, and serving profile. It will support controlled experiments—such as tokenizer or data-mixture changes—rather than simply training a model once.

## Initial scope
- Small decoder-only Transformer trained on a documented, legally usable dataset.
- Config-driven training with deterministic seeds where possible.
- Dataset inspection, deduplication, split and leakage checks.
- Checkpoint save/resume and training-state recovery.
- Validation loss, perplexity, and task-specific evaluation.
- Export and local inference endpoint.
- Model card and experiment lineage.

## Non-goals
- Training a competitive foundation model from scratch.
- Releasing copyrighted or unlicensed training corpora.
- Optimizing custom CUDA kernels in the first milestone.
- Claiming benchmark superiority from a tiny or contaminated evaluation set.

## Lifecycle
Data -> tokenizer -> model config -> training -> validation -> checkpoint -> evaluation -> artifact registry -> serving -> monitoring.

## Documentation
- [Research brief](docs/RESEARCH.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Training lifecycle](docs/TRAINING_LIFECYCLE.md)
- [Roadmap](docs/ROADMAP.md)

## Status
<badge>Research / design phase</badge>

No trained model or benchmark result is claimed yet. Initial implementation should begin with a tiny, reproducible baseline before scaling.
