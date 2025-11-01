# 🌍 ClimateNet: A Multi-Faceted Classifier for Analyzing Climate Change Discourse

**Authors:** <sup>$</sup>Tustee Mazumdar, <sup>$</sup>Adrika Chowdhury, Abu Nowshed Chy, and Tarem Ahmed || $- Equal Contribution ||

---

## 🏛️ Publication Status

This paper, *“ClimateNet: A Multi-Faceted Classifier for Analyzing Climate Change Discourse,”* has been **accepted and presented at the IEEE Region 10 Humanitarian Technology Conference (R10-HTC 2025)**.  
It is currently **in press and will be published soon in the IEEE Xplore digital library**.

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

The proposed **ClimateNet** framework follows a **hybrid multi-model architecture** that combines transformer-based feature extraction with sequential and dense learning modules for robust text classification.

Each transformer (BERT, RoBERTa, DistilBERT, ClimateBERT) is fine-tuned and followed by a BiLSTM and MLP classifier.  

- **Transformers:** Extract deep contextual features
- **BiLSTM:** Captures long- and short-term dependencies
- **MLP:** Maps learned representations to output labels


### 🧠 Pipeline Components

1. **Data Formatting:**  
   Raw social media texts and their associated labels are preprocessed and tokenized into a structured input format suitable for transformer models.

2. **Feature Extraction (BERT, RoBERTa, DistilBERT, ClimateBERT):**  
   Each transformer independently extracts deep contextual embeddings from the formatted text.  
   These embeddings capture the semantic nuances and contextual relationships in climate-related discourse.

3. **Sequential Learning (BiLSTM):**  
   The extracted features are passed through a **Bidirectional LSTM**, which models long-term dependencies by processing sequences in both forward and backward directions.  
   This step enhances temporal understanding and context retention.

4. **Classification Module (MLP):**  
   The BiLSTM outputs are fed into a **Multilayer Perceptron (MLP)** classifier, which produces the final predictions for each task.  
   Depending on the classification objective (binary or multiclass), a sigmoid or softmax activation is applied.

---

In essence, ClimateNet integrates **contextual transformers** with **temporal sequence modeling** and **dense classification layers**, enabling the framework to accurately predict multi-faceted aspects of climate change discourse across six tasks.

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

We used **ClimaConvo**,  a publicly available dataset comprising **15,309 English climate-related tweets**, annotated across the six dimensions listed above.  
Data split: **80% train / 20% test** (stratified).  
Main evaluation metric: **Macro-averaged F1-score**.

---

## 📂 Repository Structure

```bash
Notebooks/
├── Relevance/
│   ├── BERT_Relevance.ipynb
│   ├── ClimateBERT_Relevance.py
│   ├── DistilBERT_Relevance.py
│   └── RoBERTa_Relevance.py
│
├── Stance/
│   ├── BERT_Stance.ipynb
│   ├── ClimateBERT_Stance.ipynb
│   ├── DistilBERT_Stance.ipynb
│   └── RoBERTa_Stance.ipynb
│
├── Hate_Speech/
│   ├── BERT_HateSpeech.ipynb
│   ├── ClimateBERT_HateSpeech.ipynb
│   ├── DistilBERT_HateSpeech.ipynb
│   └── RoBERTa_HateSpeech.ipynb
│
├── Hate_Speech_Directions/
│   ├── BERT_Directions.ipynb
│   ├── ClimateBERT_Directions.ipynb
│   ├── DistilBERT_Directions.ipynb
│   └── RoBERTa_Directions.ipynb
│
├── Hate_Speech_Targets/
│   ├── BERT_Targets.ipynb
│   ├── ClimateBERT_Targets.ipynb
│   ├── DistilBERT_Targets.ipynb
│   └── RoBERTa_Targets.ipynb
│
└── Humor/
    ├── BERT_Humor.ipynb
    ├── ClimateBERT_Humor.ipynb
    ├── DistilBERT_Humor.ipynb
    └── RoBERTa_Humor.ipynb
```
---

Inside the `Notebooks` directory, each subdirectories correspond to a **specific classification task**, and within each folder, four transformer-based implementations are provided separately for modularity and reproducibility.
All scripts include:
- Dataset preprocessing and tokenization  
- Model fine-tuning and BiLSTM integration  
- Training, evaluation, and result saving  

---

## 💻 Installation

To replicate our experiments or explore the ClimateNet notebooks locally, please follow these steps:

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/<your-username>/ClimateNet.git
cd ClimateNet
```

### 2️⃣ Set Up the Python Environment
Use Python 3.10+

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Run the Notebooks

Upload the notebook of your choice (e.g., ```Notebooks/Stance/DistilBERT_Stance.ipynb```) to Colab and ensure the runtime is set to GPU for faster training.


## 🙏 Acknowledgment

This research builds upon the **ClimaConvo** dataset introduced by **Shiwakoti et al. (2024)** in their paper *“Analyzing the Dynamics of Climate Change Discourse on Twitter: A New Annotated Corpus and Multi-Aspect Classification”* (LREC-COLING 2024).  
We gratefully acknowledge their contribution for providing the annotated benchmark dataset that enabled our experiments and evaluation.
