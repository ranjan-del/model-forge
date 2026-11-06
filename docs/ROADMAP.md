# Roadmap

## Phase 0 — Lifecycle design
- [ ] Choose a small legally usable training corpus.
- [ ] Define artifact/experiment schemas and target hardware.
**Exit:** feasible scope and clear data rights.

## Phase 1 — Minimal decoder-only model
- [ ] Implement embeddings, causal attention, MLP, residuals, normalization, output head.
- [ ] Add shape, masking, and overfit-a-tiny-batch tests.
**Exit:** model learns a tiny fixture and passes correctness tests.

## Phase 2 — Data and training
- [ ] Add manifest-driven loading, deduplication, split/leakage audit.
- [ ] Add train/validation loop and metrics.
- [ ] Add full-state checkpoint/resume.
**Exit:** reproducible interrupted/resumed training.

## Phase 3 — Evaluation and artifacts
- [ ] Add perplexity and task probes.
- [ ] Add artifact card and lineage.
- [ ] Compare one controlled variable at a time.
**Exit:** claims supported by evaluation.

## Phase 4 — Serving
- [ ] Add local generation interface.
- [ ] Validate tokenizer/model compatibility.
- [ ] Measure latency/memory and publish model card.
**Exit:** another developer can load and evaluate the artifact.
