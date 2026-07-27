-Dutch-Name-Generator-Bigram-Language-Model
A production‑ready bigram language model that generates realistic Dutch first names.
# 🇳🇱 Dutch Name Generator with Bigram Language Model

This project is a **character-level language model** trained on a dataset of **Dutch first names**. It learns the statistical patterns of Dutch names and generates new, plausible Dutch-sounding names using a **bigram (2-gram) model**.

> **Inspired by Andrej Karpathy's ["makemore"](https://github.com/karpathy/makemore) series** — the foundational tutorial on building character-level language models from scratch.  
> Special thanks to **DeepSeek** for providing valuable technical insights and guidance during development.

---

## 🎯 Project Objective

Build a lightweight, reproducible, and explainable language model that:

- Learns character-level patterns from a real-world Dutch names dataset.
- Generates new, authentic-looking Dutch names.
- Demonstrates core NLP concepts (tokenization, bigrams, probability, sampling).
- Serves as a portfolio project showcasing data processing, modeling, and serialization skills.

---

## 📊 Dataset

- **Source**: `Top_eerste_voornamen_NL_2010.csv` from the Meertens Institute (Netherlands).
- **Size**: 1,490 unique Dutch first names.
- **Format**: CSV with semicolon (`;`) delimiter; columns: rank, name, count.
- **Preprocessing**: Extracted names, handled encoding issues (UTF-8, Latin-1 fallback), and saved as `names.txt`.

---

## 🛠️ Technologies & Tools

| Tool | Purpose |
|------|---------|
| **Python 3.10+** | Core programming language |
| **PyTorch** | Tensor operations, broadcasting, multinomial sampling |
| **Pandas / Tabulate** | Data display and table formatting |
| **Matplotlib / Seaborn** | Heatmaps and visualizations |
| **WordCloud** | Word cloud generation |
| **Pickle** | Serialization of dictionaries |
| **CSV / OS** | File handling and data ingestion |

---

## 🧠 Model Architecture (Bigram)

The model is based on a **first-order Markov assumption**:

> *"The probability of the next character depends only on the current character."*

### Workflow:

1. **Vocabulary Building** → Map characters to indices (including special characters like `é`, `ë`).
2. **Bigram Counting** → Count all adjacent character pairs (including start/end tokens `.`).
3. **Probability Matrix** → Normalize each row to get conditional probabilities.
4. **Name Generation** → Start from `.`, sample next character using `torch.multinomial`, repeat until `.` is sampled again.

---

## 📈 Key Statistics

| Metric | Value |
|--------|-------|
| Total names in dataset | 1,490 |
| Vocabulary size (including `.`) | 61 |
| Total bigrams counted | 10,899 |
| Unique bigrams | 605 |
| Most frequent bigram | `a.` (582 occurrences) |
| Least frequent bigram (non-zero) | `.Ö` (1 occurrence) |
| Average name length (generated) | ~6.15 chars |
.

---

## 📸 Sample Outputs

### Generated Dutch-like Names (temperature = 1.2):
<img width="1102" height="612" alt="image" src="https://github.com/user-attachments/assets/ee7cb51c-7a3e-4922-994d-ca7bc20febab" />

> **Note**: Temperature controls creativity. Higher temperature → more diverse/creative names. Lower temperature → more conservative names similar to the training data.

---

## 🖼️ Visualizations

### 1. Word Cloud of Generated Names (temp = 1.2)
<img width="1785" height="975" alt="wordcloud_generated_names (1)" src="https://github.com/user-attachments/assets/4c9ff8a8-5d44-4904-bb66-0aec22e7ba91" />

### 2. Probability Matrix Heatmap
<img width="1947" height="1756" alt="probability_heatmap_clean" src="https://github.com/user-attachments/assets/5ac5c5ba-7fbe-45b9-bcdb-4665be28ca97" />

### 3. Temperature Effect on Name Diversity & Length
<img width="1366" height="824" alt="temperature_effect (1)" src="https://github.com/user-attachments/assets/9b8b9485-114a-46a3-bc94-2931f8e74953" />

### 4. Length Distribution: Original vs Generated
<img width="1511" height="824" alt="length_distribution_comparison" src="https://github.com/user-attachments/assets/fc9e0bc1-0ec2-4751-8790-17b433349ab4" />

---

