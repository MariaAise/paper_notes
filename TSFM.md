Re(Visiting) Time Series Foundation Models in Finance

Eghbal Rahimikia*, Hao Ni, Weiguan Wang

Characteristics of the financial data:
- non stationary
- heterogenious
- noise-to-signal is high

  TSFM: time-series foundational models to learn generalizable **temporal** representations.

**Method**: Compared: zero-shot, fine-tuning, pre-training from scratch

**Data**:  daily excess returns for 34 years across 94 countries

**Benchmarks**: vs linear models, ensemble models, neural networks.
Tested across major markets: United States, Hong Kong, Taiwan, South Korea, Germany, the United Kingdom, India, and Australia.
  

  Main focus of TSFM: learn temporary regularities (e.g. seasonality, volatility clustering, long-memory features) as reusable representations that can be adapted to domain-specific tasks.
  
  2 types of approaches in TSFMs:

   - discrete tokenization with autoregressive decoding
   - continuous latent embeddings with regression-style objectives. 


