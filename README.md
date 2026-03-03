# LREC-2026-Dynamic-Model-Switching-to-Mitigate-Outdated-Knowledge-in-Large-Language-Models

# TaDD: Temporally-aware Dynamic Dataset (LREC 2026)

This repository contains the official dataset released with the LREC 2026 paper:

**Dynamic Model Switching to Mitigate Outdated Knowledge in Large Language Models**

Ramakrishna Pinninti, Sabyasachi Kamila, Ayan Mazumder, Mohammed Hasanuzzaman  
Accepted at LREC 2026 

---

## 📌 Overview

Large Language Models (LLMs) often generate outdated responses due to static pretraining corpora.

To support research on temporal validity detection and knowledge obsolescence, we release **TaDD (Temporally-aware Dynamic Dataset)** — a curated dataset integrating:

- Outdated and updated sentence pairs  
- Temporal validity labels  
- Semantic vs temporal update distinctions  

The dataset is designed to benchmark temporal robustness and dynamic model adaptation without requiring continual retraining.

---

**TaDD.csv**

Each instance contains:

- `Outdated_content` – Original sentence containing potentially outdated information  
- `Updated_content` – Revised sentence reflecting updated factual information  
- `Temporal_Validity_Tag` – Binary label  

### Label Definition

- **1 (Temporal Update)**  
  Substantial factual changes such as:
  - Numerical updates  
  - Date changes  
  - Status changes  
  - Named entity changes  
  - Time-sensitive modifications  

- **0 (Semantic Update)**  
  Minor revisions such as:
  - Rewording  
  - Stylistic edits  
  - Paraphrasing  
  - Punctuation adjustments  

---

## 🏷 Annotation Protocol

Annotation followed a structured two-stage process:

1. Draft suggestions generated using GPT-4.1 Mini (assistive only)
2. Final labels assigned exclusively by human annotators

Inter-annotator agreement:

- Cohen’s Kappa (κ): 0.664  
- Raw Agreement: 83.2%  

This indicates substantial agreement and confirms annotation reliability.

---

##  Intended Use

This dataset is intended for academic research on:

- Temporal validity prediction  
- Text obsolescence detection  
- Knowledge freshness evaluation    
- Temporal robustness benchmarking  

---

## 🔄 Dynamic Model-Switching Framework

![Dynamic Model-Switching Framework](figures/Dynamic model-switching framework.png)

**Figure 1.** Architecture of the proposed Dynamic Model-Switching framework introduced in our LREC 2026 paper.  
Given an input \(x\), the system evaluates two temporally specialized generators:

- **Big_Model (M₁)** – trained on historical data  
- **Small_Model (M₂)** – fine-tuned on recent data  

A lightweight switch model selects the most temporally appropriate model based on:

- Contextual relevance reward \(r_{context}\)  
- An adaptive temporal validity threshold \(τ\)  

This design enables temporally-aware generation without requiring continual retraining of the base models.
