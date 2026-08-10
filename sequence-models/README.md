# sequence-models

Sequence-modeling architectures — alternatives and complements to attention.

| File | Topic |
| --- | --- |
| [`ssm_tutorial.html`](ssm_tutorial.html) | State-space models from scratch. RNN refresher, the four matrices (A, B, C, D), the recurrent / convolutional dual modes that make SSMs both cheap at inference and fast to train, SSM-vs-Transformer trade-offs, interactive 1D SSM playground, and a deep-dive tab on where the non-linearity actually lives in a stacked SSM. |
| [`speculative_decoding_tutorial.html`](speculative_decoding_tutorial.html) | Speculative decoding from scratch. Full correctness proof of modified rejection sampling, the `(1 - α^(γ+1))/(1-α)` expected-tokens formula, SpecInfer-style tree drafts with multi-round rejection, EAGLE / EAGLE-2 feature-level drafting and dynamic trees. Interactive playground for acceptance geometry and tree visualization. |
| [`dflash_training_tutorial.html`](dflash_training_tutorial.html) | How DFlash's block-diffusion draft model is trained from a frozen target model (arXiv:2602.06036): self-distilled data curation, target-feature fusion, anchor sampling, packed block-diagonal attention, KV injection at every draft layer, and the position-weighted loss tied to greedy-prefix acceptance. Interactive demos for block construction, the attention mask, and the loss decay. |
