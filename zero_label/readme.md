Absolute Zero: Reinforced Self-play Reasoning with Zero Data

[hf page](https://huggingface.co/papers/2505.03335)

[pdf](https://arxiv.org/pdf/2505.03335)

**Lingo:**

**Reinforcement learning**: a framework where agents (model) learn from the environment by interacting with it (trial and error) and receiving rewards (positive or negative) as unique feedback.

Agent is in S0, takes action A0, receives a reward R0, moves to state S1...

**Reward hypothesis**: maximise the expected reward (**expected cumulative reward**)

**Markov decision process**: to decide on the next step the agent needs to consider only the current state, not all the previous states (**Markov Property**)

**State s**: a complete description of the state of the world, fully observed environment.

**Reasoning models**: models optimized to think through a problem step-by-step and arrive at logically consistent, verifiable solutions.

**Reinforcement learning with verifiable rewards (RLVR)**: training reasoning models with programmatic verifiers instead of human labels.
