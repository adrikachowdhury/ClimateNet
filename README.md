# 🌍 ClimateNet: A Multi-Faceted Classifier for Analyzing Climate Change Discourse

**Authors:** Tustee Mazumdar and Adrika Chowdhury (equal contribution), Abu Nowshed Chy, and Tarem Ahmed

---

## 🧩 Overview

**ClimateNet** is a **multi-task text classification framework** designed to analyze the multifaceted discourse surrounding **climate change on social media**. It leverages **transformer-based contextual embeddings (BERT, RoBERTa, DistilBERT, ClimateBERT)** integrated with a **Bidirectional LSTM (BiLSTM)** and a **Multilayer Perceptron (MLP)** classifier to capture both semantic and sequential dependencies in textual data.  

The model aims to uncover diverse perspectives—including stance, relevance, humor, and hate—within climate-related conversations, aligning with **UN Sustainable Development Goal (SDG) 13: Climate Action**.

---

## 🧠 Research Motivation

Online discussions on climate change reflect a range of public opinions—from support and opposition to humor and hostility. Understanding these nuances helps policymakers, researchers, and organizations promote informed awareness and counter harmful narratives.  

However, analyzing such short, noisy, and imbalanced microblog data (e.g., tweets) is challenging. ClimateNet addresses these issues through:
- **Contextualized embeddings** from transformers  
- **Sequential learning** via BiLSTM  
- **Class imbalance handling** using weighted cross-entropy and oversampling  
- **Multi-aspect classification** across six tasks  

---

## ⚙️ Architecture

Input Tweets → Preprocessing → Transformer Embedding
→ BiLSTM (Sequential Learning)
→ MLP Classifier → Predicted Label

Each transformer (BERT, RoBERTa, DistilBERT, ClimateBERT) is fine-tuned and followed by a BiLSTM and MLP classifier.  

- **Transformers:** Extract deep contextual features  
- **BiLSTM:** Captures long- and short-term dependencies  
- **MLP:** Maps learned representations to output labels  

---

## 📚 Tasks

ClimateNet performs **six independent NLP classification tasks** on the *ClimaConvo* dataset:

| Task | Description | Label Type |
|------|--------------|-------------|
| **Relevance Detection** | Classify whether a tweet is related to climate change | Binary (0–Non-relevant, 1–Relevant) |
| **Stance Detection** | Identify stance: Support, Oppose, or Neutral | Multiclass (0–Support, 1–Oppose, 2–Neutral) |
| **Hate Speech Detection** | Detect presence of hate content | Binary (0–Non-hate, 1–Hate) |
| **Direction of Hate Speech** | Determine if hate is direct or indirect | Binary (0–Undirected, 1–Directed) |
| **Target of Hate Speech** | Identify if hate targets individuals, organizations, or communities | Multiclass (0–Individual, 1–Organization, 2–Community) |
| **Humor Detection** | Detect humorous or sarcastic tone | Binary (0–Non-humor, 1–Humor) |

---

## 🧾 Dataset

We used **ClimaConvo** — a publicly available dataset comprising **15,309 English climate-related tweets**, annotated across the six dimensions listed above.  
Data split: **80% train / 20% test** (stratified).  
Main evaluation metric: **Macro-averaged F1-score**.

---

## 📂 Repository Structure

Notebooks/<b>
├── Relevance/
│ ├── BERT.py
│ ├── ClimateBERT.py
│ ├── DistilBERT.py
│ └── RoBERTa.py
│
├── Stance/
│ ├── BERT.py
│ ├── ClimateBERT.py
│ ├── DistilBERT.py
│ └── RoBERTa.py
│
├── Hate_Speech/
│ ├── BERT.py
│ ├── ClimateBERT.py
│ ├── DistilBERT.py
│ └── RoBERTa.py
│
├── Hate_Speech_Directions/
│ ├── BERT.py
│ ├── ClimateBERT.py
│ ├── DistilBERT.py
│ └── RoBERTa.py
│
├── Hate_Speech_Targets/
│ ├── BERT.py
│ ├── ClimateBERT.py
│ ├── DistilBERT.py
│ └── RoBERTa.py
│
└── Humor/
├── BERT.py
├── ClimateBERT.py
├── DistilBERT.py
└── RoBERTa.py

---


Each directory corresponds to a **specific classification task**, and within each folder, four transformer-based implementations are provided separately for modularity and reproducibility.  
All scripts include:
- Dataset preprocessing and tokenization  
- Model fine-tuning and BiLSTM integration  
- Training, evaluation, and result saving  

---

## 🙏 Acknowledgment

This research builds upon the **ClimaConvo** dataset introduced by **Shiwakoti et al. (2024)** in their paper *“Analyzing the Dynamics of Climate Change Discourse on Twitter: A New Annotated Corpus and Multi-Aspect Classification”* (LREC-COLING 2024).  
We gratefully acknowledge their contribution for providing the annotated benchmark dataset that enabled our experiments and evaluation.
