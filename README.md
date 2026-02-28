# KPI-Aware Financial Summarization using Long-Context Transformers

Research project investigating long-context transformer models for abstractive summarization of SEC 10-K Management Discussion & Analysis (MD&A) sections with domain-specific KPI-aware evaluation.

---

## 📌 Problem Statement

SEC 10-K MD&A sections are lengthy, jargon-heavy financial narratives.

Generic summarization models often:
- Truncate long inputs
- Miss critical Key Performance Indicators (KPIs)
- Produce fluent but financially incomplete summaries

This project investigates whether long-context transformers improve financial fidelity, not just lexical overlap.

---

## 🗂 Datasets

Two datasets were aligned using CIK and filing date:

1. **Summarized 10K-MDA**
   - Human abstractive summaries
   - Document-level KPI sets
   - Compact MD&A segments

2. **Financial-Reports-SEC**
   - Full-length 10-K filings
   - Section-level metadata
   - Complete MD&A reconstruction

Final benchmark includes:
- Full MD&A document (long context)
- Gold summary
- Normalized KPI set

Total Samples: 153  
Train: 122  
Validation: 15  
Test: 16  

---

## 🧠 Models Compared

### Short-Context Baselines
- BART
- BART-v2 (tuned)
- PEGASUS
- PEGASUS-v2

### Long-Context Transformers
- LED
- LED-v2
- LED-full
- BigBird-Pegasus
- LongT5

All models trained under:
- Single NVIDIA T4 GPU (16GB)
- Batch size 1
- Gradient accumulation
- One epoch fine-tuning

---

## 📊 Evaluation Metrics

### Lexical
- ROUGE-1 / ROUGE-2 / ROUGE-L
- BLEU

### Semantic
- Sentence-transformer cosine similarity

### Domain-Specific KPI Metrics
- KPI Precision
- KPI Recall
- KPI F1
- Hallucinated KPIs
- Missing KPIs

### Compression Ratio
Summary length / Document length

---

## 📈 Key Results

- **BART-v2 achieved best ROUGE and BLEU**
- Long-context models did NOT significantly outperform dense models
- KPI-F1 remained low (~0.06–0.07) across all models
- Models omitted KPIs more often than hallucinating them
- Semantic similarity higher than lexical metrics suggest

### Insight:
High ROUGE ≠ Financial Faithfulness

Standard summarization metrics fail to capture domain-critical information.

---

## 🧪 KPI-Level Findings

- Avg ground-truth KPIs per document ≈ 3
- Models mention ≈ 0.25 KPIs per summary
- Majority of KPIs are dropped
- Hallucination rate is low but non-zero
- Missing KPIs are the primary weakness

---

## 🏗 Pipeline

1. Data alignment via CIK + filing date
2. MD&A reconstruction from section labels
3. KPI normalization (controlled vocabulary)
4. Tokenizer-aware truncation
5. Model fine-tuning
6. Multi-metric evaluation
7. KPI-level analysis

---

## 🛠 Tech Stack

- Python
- PyTorch
- HuggingFace Transformers
- Datasets
- Evaluate / SacreBLEU
- Pandas / NumPy / scikit-learn
- Kaggle GPU environment

---

## 🎯 Contributions

✔ Built long-document financial summarization benchmark  
✔ Designed KPI-aware evaluation metric  
✔ Compared long vs short context transformers  
✔ Quantified hallucination vs omission trade-off  
✔ Demonstrated gap between ROUGE and financial utility  

---

## 🔮 Future Work

- Constrained decoding for KPI preservation
- Joint KPI extraction + summarization heads
- Reinforcement learning objectives for KPI fidelity
- Retrieval-augmented summarization
- Larger GPU training schedules

---

## 📜 License

MIT License

---

## ⚠ Disclaimer

For academic and research purposes only.  
Not intended for financial advisory use.
