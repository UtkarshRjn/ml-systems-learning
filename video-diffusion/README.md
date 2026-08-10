# video-diffusion

Video diffusion and sparse-attention systems — mostly tracking work from
[Hao Zhang's lab](https://cseweb.ucsd.edu/~haozhang/) at UCSD plus related
inference-acceleration papers.

| File | Topic |
| --- | --- |
| [`fastvideo_lesson.html`](fastvideo_lesson.html) | FastVideo framework — what it is, how it parallelizes long-context video generation across GPUs. |
| [`vsa_varlen_simple.html`](vsa_varlen_simple.html) | Short intro to variable-length Video Sparse Attention (VSA). |
| [`vsa_varlen_tutorial.html`](vsa_varlen_tutorial.html) | Deeper tutorial on VSA varlen kernel design — how the varlen layout is packed, how the sparse mask is materialized, what the kernel actually does on the GPU. |
| [`chipmunk_tutorial.html`](chipmunk_tutorial.html) | Chipmunk — sparse-attention and sparse-MLP acceleration for video diffusion inference. |
