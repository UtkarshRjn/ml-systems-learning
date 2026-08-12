# ml-systems-learning

Self-made HTML tutorials and lesson notes I build while studying papers and
open-source code in efficient ML systems — mostly around **video diffusion**,
**diffusion language models**, **state-space models**, and the **GPU
programming** that underpins all of it.

These are personal learning artifacts: I write them as I read to internalize
the ideas. Sharing publicly in case they help anyone working through the same
material.

## Contents

### [`foundations/`](foundations/) — ML fundamentals
| File | Topic |
| --- | --- |
| [`losses_tutorial.html`](foundations/losses_tutorial.html) | Tour of ML loss functions: MSE/MAE/Huber, entropy, cross-entropy, KL divergence (forward vs. reverse), JS/Wasserstein, hinge/focal, contrastive/triplet/InfoNCE, GAN/VAE losses. Interactive canvas demos throughout and a 6-question quiz. |

### [`gpu-programming/`](gpu-programming/) — GPU & CUDA
| File | Topic |
| --- | --- |
| [`cuda_cpp_tutorial.html`](gpu-programming/cuda_cpp_tutorial.html) | A complete CUDA C++ background-knowledge tutorial — structured around the 6 reusable patterns (element-wise, stencil, reduction, scan, matmul tile, online softmax) plus tensor cores, MXFP4/8 + NVFP4 quantized GEMM, GPU graph algorithms, finite-field arithmetic, FlashAttention. Built from a survey of all 84 problems on [tensara.org](https://tensara.org/problems), with 1D convolution as the worked end-to-end example. |

### [`sequence-models/`](sequence-models/) — Sequence-modeling architectures
| File | Topic |
| --- | --- |
| [`ssm_tutorial.html`](sequence-models/ssm_tutorial.html) | State-space models from scratch. RNN refresher, the four matrices (A, B, C, D), the recurrent / convolutional dual modes, SSM-vs-Transformer trade-offs, an interactive 1D SSM playground, and a deep-dive tab on where the non-linearity actually lives. |
| [`speculative_decoding_tutorial.html`](sequence-models/speculative_decoding_tutorial.html) | Speculative decoding from scratch. Full correctness proof of modified rejection sampling, the `(1 - α^(γ+1))/(1-α)` expected-tokens formula, SpecInfer-style tree drafts with multi-round rejection, EAGLE / EAGLE-2 feature-level drafting and dynamic trees. Interactive playground for acceptance geometry and tree visualization. |
| [`dflash_training_tutorial.html`](sequence-models/dflash_training_tutorial.html) | How DFlash's block-diffusion draft model is trained from a frozen target model (arXiv:2602.06036): self-distilled data curation, target-feature fusion, anchor sampling, packed block-diagonal attention, KV injection at every draft layer, and the position-weighted loss tied to greedy-prefix acceptance. Interactive demos for block construction, the attention mask, and the loss decay. |
| [`dspark_tutorial.html`](sequence-models/dspark_tutorial.html) | DSpark, DeepSeek's production speculative-decoding stack (arXiv:2607.05147). Why parallel drafters win position 1 but decay after (multi-modal collision), the semi-autoregressive fix (DFlash backbone + low-rank Markov / RNN transition head), the confidence head with its analytical `1 − ½‖p_d − p_t‖₁` labels and Sequential Temperature Scaling, and the hardware-aware prefix scheduler that maximizes `Θ = τ·SPS(B)` — including the Appendix-A selection-bias counterexample and the two-steps-prior causal barrier used in the DeepSeek-V4 deployment. Interactive demos for acceptance-decay curves, the Markov-head collision fix, and the greedy admission loop under load. |

### [`video-diffusion/`](video-diffusion/) — Video diffusion & sparse attention
| File | Topic |
| --- | --- |
| [`fastvideo_lesson.html`](video-diffusion/fastvideo_lesson.html) | FastVideo framework (Hao lab) — what it is, how it parallelizes long-context video generation. |
| [`vsa_varlen_simple.html`](video-diffusion/vsa_varlen_simple.html) | Short intro to variable-length Video Sparse Attention. |
| [`vsa_varlen_tutorial.html`](video-diffusion/vsa_varlen_tutorial.html) | Deeper tutorial on VSA varlen kernel design. |
| [`chipmunk_tutorial.html`](video-diffusion/chipmunk_tutorial.html) | Chipmunk — sparse-attention / sparse-MLP acceleration for video diffusion inference. |

### [`diffusion-llms/`](diffusion-llms/) — Diffusion language models
| File | Topic |
| --- | --- |
| [`fast_dllm_tutorial.html`](diffusion-llms/fast_dllm_tutorial.html) | Fast-dLLM — accelerating diffusion language model inference. |
| [`dkv_cache_tutorial.html`](diffusion-llms/dkv_cache_tutorial.html) | dKV-Cache — KV caching adapted for diffusion language models. |

### [`fine-tuning/`](fine-tuning/) — Parameter-efficient fine-tuning
| File | Topic |
| --- | --- |
| [`lora_tutorial.html`](fine-tuning/lora_tutorial.html) | LoRA from scratch — the original Hu et al. equation, initialization trick, rank/alpha choices, and the modern (2025–2026) consensus on which modules to target. Family tree of follow-ups: QLoRA, DoRA, LoRA+, rsLoRA, VeRA, PiSSA, LoftQ, AdaLoRA, LongLoRA. Serving section on merging vs multi-tenant (S-LoRA / vLLM multi-LoRA). Interactive parameter-count calculator across Llama models, rsLoRA vs LoRA scaling visualizer, and an 8-question quiz. |

### [`serving/`](serving/) — Inference-serving economics
| File | Topic |
| --- | --- |
| [`tau_gate_game.html`](serving/tau_gate_game.html) | Speculative decoding × multi-tenant LoRA serving, as a six-level playable derivation. Why the `(1 - α^(K+1))/(1-α)` series saturates, why a verify pass covers K+1 positions rather than K, the roofline ratio `max(1, B·P/B*) / max(1, B/B*)` dissected term by term across all three regimes — including the middle band where speculation is compute-bound but plain decoding is not — the S-LoRA adapter tax, and the break-even condition `τ_L/τ_G > 1 + A/C`. Live accept/reject sampler, cost ledgers, speedup-vs-batch charts, scored checkpoints. Sits between [`speculative_decoding_tutorial.html`](sequence-models/speculative_decoding_tutorial.html) and [`lora_tutorial.html`](fine-tuning/lora_tutorial.html): those cover the two mechanisms, this covers what they cost each other. |

## How to view

Open any `.html` directly in your browser — they're self-contained (single
file, embedded CSS/JS, no build step).

## Acknowledgements

Material is based on research and open-source code from:

- [Hao Zhang's lab](https://cseweb.ucsd.edu/~haozhang/) at UCSD — FastVideo, video sparse attention, distributed training, video diffusion systems
- [Dan Fu's lab](https://www.danfu.org/) at UCSD — state-space models, efficient sequence modeling
- [Z Lab (Zhijian Liu)](https://z-lab.ai/) at UCSD — DFlash, block-diffusion speculative decoding
- [DeepSeek-AI](https://www.deepseek.com/) — DSpark, confidence-scheduled speculative decoding, and the DeepSpec training repo
- The respective authors of Chipmunk, Fast-dLLM, dKV-Cache, and the wider efficient-ML community

All credit for the underlying ideas goes to the original authors. Any errors
in these notes are mine.
