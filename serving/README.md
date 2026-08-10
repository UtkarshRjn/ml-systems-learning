# serving

Inference-serving economics — what a technique costs once it has to run inside
a real batched, multi-tenant server rather than on a single sequence.

| File | Topic |
| --- | --- |
| [`tau_gate_game.html`](tau_gate_game.html) | Speculative decoding × multi-tenant LoRA serving, built as a six-level playable derivation. Why τ = (1 − α^(K+1))/(1 − α) saturates, why a verify pass covers K+1 positions and not K, the roofline ratio `max(1, B·P/B*) / max(1, B/B*)` dissected term by term across all three regimes, the S-LoRA adapter tax, and the break-even condition τ_L/τ_G > 1 + A/C that decides whether per-repo draft adapters are worth building at all. Live accept/reject sampler, cost ledgers, speedup-vs-batch charts, and a scored final decision where acceptance genuinely improves and you still have to kill the project. |
