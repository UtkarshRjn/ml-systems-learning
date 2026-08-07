# ml-systems-learning

A collection of self-made HTML tutorials and lesson notes I built while studying
work from **Dan Fu's lab** and **Hao Zhang's lab** at UCSD — primarily around
efficient ML systems, video diffusion, sparse attention, and state-space models.

These are my personal learning artifacts: I make them as I read papers and code
to internalize the ideas. Sharing publicly in case they help anyone else
working through the same material.

## Contents

| File | Topic |
| --- | --- |
| [`ssm_tutorial.html`](ssm_tutorial.html) | State-space models walkthrough |
| [`fastvideo_lesson.html`](fastvideo_lesson.html) | Notes on the FastVideo framework (Hao lab) |
| [`vsa_varlen_simple.html`](vsa_varlen_simple.html) | Short intro to variable-length VSA (Video Sparse Attention) |
| [`vsa_varlen_tutorial.html`](vsa_varlen_tutorial.html) | Deeper tutorial on VSA varlen kernel design |
| [`losses_tutorial.html`](losses_tutorial.html) | Tour of ML loss functions: MSE/MAE/Huber, entropy, cross-entropy, KL divergence (forward vs. reverse), hinge/focal, contrastive/triplet/InfoNCE, GAN/VAE losses |
| [`dflash_training_tutorial.html`](dflash_training_tutorial.html) | How DFlash's block-diffusion draft model is trained from a frozen target model: self-distilled data, target-feature fusion, anchor sampling, block packing, KV injection, position-weighted loss |

## How to view

Just open any `.html` file directly in your browser, or browse via GitHub Pages
if enabled.

## Acknowledgements

Material is based on research and open-source code from:

- [Dan Fu's lab](https://www.danfu.org/) — state-space models, efficient sequence modeling
- [Hao Zhang's lab](https://cseweb.ucsd.edu/~haozhang/) — FastVideo, distributed training, video diffusion systems
- [Z Lab (Zhijian Liu), UC San Diego](https://z-lab.ai/) — DFlash: block diffusion for speculative decoding ([arXiv:2602.06036](https://arxiv.org/abs/2602.06036))

All credit for the underlying ideas goes to the original authors. Any errors in
these notes are mine.
