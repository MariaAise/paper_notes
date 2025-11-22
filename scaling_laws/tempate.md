## Paper

Hoffmann et al. (2022). Training Compute-Optimal Large Language Models.
DeepMind.

## Main idea

For a fixed compute budget, models should be much smaller and trained on many more tokens than GPT-3-like paradigms assumed. The paper derives new empirical scaling laws showing that data, not parameters, is the primary driver of performance under realistic compute constraints.

## Problem

The pre-Chinchilla paradigm over-invested in parameter count and under-invested in tokens, leading to:

suboptimal compute use

unnecessary inference cost

poor training efficiency

worse generalisation
Chinchilla provides the first compute-optimal tradeoff between model size and training tokens.

## So what

Direct impact on:

Scaling strategy: determines how to allocate compute for next-gen models.

Training efficiency: fewer parameters → cheaper to serve.

Data strategy: establishes target token budgets.

Model performance: better loss for the same compute.
This paper defines the modern training regime for Gemini-class, GPT-4-class, Claude-class models.

## Method

Train dozens of transformer models across a grid of sizes (70M → 16B params).

Vary token budgets from 5B → 500B.

Fit empirical scaling laws relating loss to:

model size 

dataset size 

compute 

Derive optimal 

Show that GPT-3-style models were ~4× under-trained.

## Results

Optimal scaling line is D ≈ 20 × N tokens.

Models should be ~4× smaller for the same compute.

Chinchilla (70B tokens, 70B params) matches/exceeds GPT-3-175B performance.

Compute-optimal models use more data, fewer parameters.

Clear diminishing returns from oversized models trained on too few tokens.

## Limitations

Based on dense transformers only.

Token quality not deeply analysed.

Assumes static data distribution.

Does not address long-context or multimodal scaling.

Scaling regime may shift as architectures evolve (MoEs, hybrids, recurrent transformers).

## When to use

If you are working on:

domain adaptation in finance

long-context specialist models

efficient training for experimental models

Then Chinchilla provides:

the baseline compute–data ratio you must respect

a rationale for prioritising more tokens over bigger models

a check: if you fine-tune/extend a model on too little domain data, you de-optimalise it

## Implementation Notes

If reproducing or adapting the results:

ensure dataset size aligns with parameter count (~20 tokens per parameter)

batch size scaling crucial — instability emerges when b < 32K tokens

LR decay schedule follows square-root scaling with compute

training stability improves if warmup >2% of total steps

## Takeaway

Prefer token-rich regimes over parameter-rich regimes.

If compute-limited, shrink the model and increase dataset size.

When designing domain adaptation experiments, you must check for token scarcity.

Use this scaling law as the reference line; deviations must be justified.

Incorporate Chinchilla regime when benchmarking or designing new model families.
