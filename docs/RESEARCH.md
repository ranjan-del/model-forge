# Research brief — Model Forge

## 1. Problem statement
A useful model-training project should demonstrate more than forward/backward passes. It should make the complete lifecycle inspectable and reproducible, including dataset governance, tokenizer/model compatibility, optimization, checkpoint recovery, evaluation, and serving.

## 2. Prior art
- **Attention Is All You Need:** foundational Transformer architecture.
- **nanoGPT:** compact educational GPT training code; useful reference, but a direct clone is not a differentiator.
- **Hugging Face Transformers / Datasets / Tokenizers:** production-oriented model and data ecosystem.
- **LitGPT:** training and fine-tuning workflows across model families.
- **Megatron-LM:** large-scale model training and parallelism.
- **PyTorch:** tensor/autograd/training primitives.

The project must document what it borrows and what it adds. Novelty should be framed as lifecycle traceability and controlled experimentation, not a new Transformer architecture unless research later supports one.

## 3. Questions to investigate
- How do data cleaning and deduplication affect train/validation leakage?
- How do tokenizer changes alter sequence length, training throughput, and learning curves?
- How do batch size, sequence length, optimizer, learning-rate schedule, and precision affect stability?
- What is lost when a checkpoint saves weights but not optimizer/scheduler/RNG state?
- How do validation loss and perplexity relate—or fail to relate—to downstream task behavior?
- What is the smallest serving path that preserves tokenizer/config/artifact compatibility?

## 4. Hypotheses
- H1: Reproducibility requires capturing more than model weights: data manifest, tokenizer, config, code revision, optimizer/scheduler, and RNG state.
- H2: Data leakage and near-duplicate contamination can make validation metrics misleading.
- H3: Tokenizer and data-mixture choices affect both training efficiency and model behavior.
- H4: Small-model benchmark scores have high variance and should be reported with sample sizes and uncertainty.
- H5: Model artifact lineage can prevent deployment mismatches between weights, tokenizer, and generation config.

## 5. Data plan
Start with a small corpus whose license and permitted use are clear. Record source/version, license, acquisition date, preprocessing, deduplication, language/domain composition, and split method. Avoid bundling source text if redistribution is not permitted. Create synthetic fixtures for tests.

## 6. Evaluation
- Training/validation loss and perplexity with exact tokenization details.
- Data leakage checks and near-duplicate overlap.
- Small task suite appropriate to the model's scale and training data.
- Calibration and generation behavior where relevant.
- Repeated seeds or multiple runs when comparing configurations.
- Qualitative error analysis, with limitations.

Never compare perplexity across incompatible tokenizers or corpora as if directly comparable.

## 7. Engineering contribution
Model Forge will provide:
1. a config-driven training lifecycle;
2. complete checkpoint/resume semantics;
3. dataset and tokenizer lineage;
4. evaluation manifests and artifact cards;
5. a simple serving interface that validates artifact compatibility;
6. experiment comparisons with controlled variables.

## 8. References
- Transformer paper: https://arxiv.org/abs/1706.03762
- nanoGPT: https://github.com/karpathy/nanoGPT
- LitGPT: https://github.com/Lightning-AI/litgpt
- Hugging Face Transformers: https://github.com/huggingface/transformers
- Hugging Face Datasets: https://github.com/huggingface/datasets
- Megatron-LM: https://github.com/NVIDIA/Megatron-LM
- PyTorch: https://pytorch.org/

Check current APIs, licenses, and model/dataset cards before adopting any upstream assets.
