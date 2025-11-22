## Scaling Laws & Compute-Optimal Training

- parameter scaling

- data scaling

- compute-optimal training

- mixture-of-experts scaling

- long-context scaling

- inference-time scaling

- data quality scaling (modern)

----------------

1. Kaplan et al., 2020 — Scaling Laws for Neural Language Models

(OpenAI)
The original transformer scaling law paper.
Read for:

loss ∝ N^−α behaviour

dataset vs model vs compute scaling

early “50% rule” intuition
Still required reading.

2. Hoffmann et al., 2022 — Training Compute-Optimal Large Language Models (Chinchilla)

(DeepMind)
The compute-optimal breakthrough.
Read for:

L ∝ N (data ≈ 20× more important than assumed)

the death of “undertrained giants”

the most structurally important scaling paper yet

This is absolutely mandatory.

3. Henighan et al., 2020 — Scaling Laws for Autoregressive Generative Modeling

(OpenAI)
Broadens scaling law concepts beyond transformers.
Read for:

multimodal scaling

entropy / perplexity relationships

how loss components scale differently

Still useful for multimodal or financial modelling with multiple distributions.

4. Villalobos et al., 2022/2023 — Tensor Programs V / VI / VII (Neural Scaling Revisited)

(DeepMind + Google)
These papers explain why scaling laws exist mathematically.
Read for:

theory behind emergent behaviour

how architecture affects scaling

trainability vs expressivity

This is gold for interviews and research.

5. Muennighoff et al., 2024 — Scaling Data Quality for LLM Pretraining

(EleutherAI + Meta + Google + HuggingFace)
THE modern correction: data quality scales better than raw size.
Read for:

deduplication effects

quality-filtered corpora

compute-optimal training with quality weighting

This is extremely relevant to Two Sigma (curated financial text).

6. DeepSeek 2024/2025 — DeepSeek V2: Scaling Mixture-of-Experts Efficiently

(DeepSeek AI)
The new reference for MoE scaling.
Read for:

expert routing stability

compute savings vs FLOPs neutrality

how to scale sparse models to frontier sizes

inference scaling under sparse routing

This is the MoE scaling law paper for 2024–2025.

7. Dao et al., 2024 — FlashAttention-2/3 Reports & Blog Notes

(Together + Stanford)
Shockingly important for scaling because attention IO-efficiency determines compute-optimal training.
Read for:

IO-bound vs FLOP-bound training

how long-context scaling depends on memory bandwidth

attention kernel scaling

Not a pure “scaling law paper,” but required for compute scaling understanding.

**8. OpenAI Technical Report 2024 — Frontier Model Training Lessons

(“GPT-4 era practices”, no direct GPT-4 paper)**
This is semi-public in fragments.
Read blog + associated reports (evals, safety, system card).
Important for:

how inference cost scales

how alignment data grows with model size

how context scaling interacts with inference budget

This gives the only modern look at inference-time scaling.

Optional but extremely valuable (9–10)
9. “Scaling Laws for Reward Models” (Anthropic, 2023–2024)

Important if you will do preference learning + scale RM training.

10. “Scaling up Online RL for LLMs / RLAIF Scaling” (Anthropic, 2024)

Useful for understanding alignment compute scaling.
