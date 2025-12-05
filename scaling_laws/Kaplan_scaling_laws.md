Kaplan et al., 2020 — Scaling Laws for Neural Language Models
(OpenAI) 

**Aim**

Training budget is finite: how to allocate it efficienty  (optimization)

**Method**
Used cross entropy loss to track the dependence between performance and data size, model size and compute time

**Findings**

**Significant** effect of data size, model size and compute time.

**Insignificant**: network architecture (deapth/width)  


**Follow**:
Larger models are sample efficient -> can be trained on smaller datasets and stop significantly before convergence

