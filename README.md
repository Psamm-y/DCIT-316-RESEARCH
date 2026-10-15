# DCIT316 Research Project: Social Media Mining

## Project Title
**Cross-Platform Stance and Sentiment Shift Detection for Code-Mixed Social Media Discourse**

## Author
* **Name:** Samuel Amoako Ampadu
* **Student ID:** 22024585
* **Course:** DCIT316 – Computational Models for Social Media Mining

---

## Project Overview
Standard sentiment analysis and NLP architectures suffer significant performance degradation when applied to low-resource, code-mixed social media microtext (e.g., English blended with Ghanaian Pidgin and Twi). This repository implements a dual-stream computational model that fuses $n$-gram TF-IDF textual representations with directed social network graph topologies (PageRank centrality on $G=(V,E)$) to detect dynamic stance drift across online communities.

---

## Repository Contents
* `DCIT316_Research_Project.ipynb`: Executable Jupyter Notebook containing data preprocessing, PageRank graph construction, feature fusion, model training, evaluation metrics, and visualization plots.
* `main.py`: Standalone Python execution script for the dual-stream model pipeline.
* `README.md`: Project documentation, setup instructions, ethics statement, and disclosure.

---

## Reproduction Steps
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/Psamm-y/DCIT-316-RESEARCH.git](https://github.com/Psamm-y/DCIT-316-RESEARCH.git)
   cd DCIT-316-RESEARCH
   ```
   
2. Set Up Virtual Environment (Eecommended)
Bash
```bash
# On Windows
python -m venv venv
.\venv\Scripts\activate
```
```bash
# On macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

3. Install Required Dependencies
Install the required core libraries directly:

```bash
pip install pandas numpy networkx matplotlib scikit-learn
```

4. Execute via Python Script
To run the full end-to-end pipeline and print metrics directly in your terminal:

```bash
python main.py
```

5. Execute via Interactive Jupyter Notebook
To view step-by-step code execution, markdown documentation, and interactive graph plots:
    1. Open VS Code or Jupyter Lab.

    2. Open DCIT316_Research_Project.ipynb.

    3. Select your Python kernel and click Run All.


##
## Literature Matrix

| Citation & Author | Key Focus / Topic | Methodology Used | Identified Research Gap | Our Project Contribution |
| :--- | :--- | :--- | :--- | :--- |
| **Çöltekin (2020); Sanguinetti et al. (2020)** | Microtext and Dialectal Informal NLP | Rule-based preprocessing & standard tokenizers | Evaluated primarily on European monolingual microtext; failed on West African slang. | Implements localized slang mapping and $n$-gram TF-IDF bigram extraction for Ghanaian Pidgin/Twi. |
| **Blei et al. (2003); Grootendorst (2022)** | Topic Extraction & Contextual Embeddings | LDA & BERTopic (class-based TF-IDF) | Topic models analyze text semantics but ignore network user influence. | Combines contextual text features with structural graph centrality metrics. |
| **Blondel et al. (2008); Newman (2010)** | Network Community & Diffusion | Louvain Algorithm & PageRank Centrality | Graph models analyze network structure but ignore text stance/polarity. | Fuses PageRank scores directly into the textual feature vector matrix ($X_{fused} = [X_{text} \mid P]$). |


##
## Data Card & Model Card

### Data Card
* **Corpus Composition:** Code-mixed social media text (English + Ghanaian Pidgin + Twi).
* **Target Categories:** Multi-class stance classification (1: In Favor, 0: Against).
* **Graph Formalization:** Directed graph $G = (V, E)$ where nodes ($V$) represent user IDs and directed edges ($E$) represent reply/mention interactions.
* **Privacy & Anonymization:** All raw usernames are anonymized into synthetic user identifiers (`user_1`, `user_2`, etc.). No private messages, passwords, or PII are stored.

### Model Card
* **Architecture:** Dual-Stream Text-Graph Classifier (Bigram TF-IDF + PageRank Feature Fusion + Logistic Regression).
* **Feature Dimensions:** $X_{text} \in \mathbb{R}^{n \times d}$ concatenated with PageRank vector $P \in \mathbb{R}^{n \times 1}$ resulting in $X_{fused} \in \mathbb{R}^{n \times (d+1)}$.
* **Baseline Comparison:** Evaluated against a text-only Logistic Regression baseline to measure the isolated metric lift provided by network topology.


##
## Failure Log & Process Notes
* **Issue 1 (Tokenization Degradation):** Standard word-level tokenizers treated concatenated dialectal terms as out-of-vocabulary noise. *Fix:* Implemented character and word bigrams (`ngram_range=(1,2)`) to capture sub-word dialect structures.
* **Issue 2 (Disconnected Network Components):** Isolated users without interaction edges yielded undefined centrality scores. *Fix:* Implemented fallback default smoothing (`.fillna(0)`) for unlinked user nodes.

##
## Reproducibility Checklist
- [x] Executable source code (`main.py`) uploaded and tested locally.
- [x] Jupyter Notebook (`DCIT316_Research_Project.ipynb`) uploaded with pre-rendered visual outputs and model logs.
- [x] Dependencies clearly defined in installation instructions.
- [x] Theoretical math equations ($G=(V,E)$, PageRank matrix fusion) fully specified.
- [x] Synthetic dataset provided directly within scripts for instantaneous single-click reproduction.

##
## Ethics Statement & AI Use Disclosure

### Ethics Statement
This study adheres to responsible social media mining practices. All data processed represents public interactions used strictly for academic evaluation. No private user data was scraped, stored, or distributed.

### AI Assistance Disclosure
* **Usage Scope:** Generative AI tools were utilized to assist with initial code structural planning, LaTeX syntax formatting, and report layout design.
* **Verification:** All core code implementation, matrix operations, script executions, graph renderings, and evaluation outputs were manually audited, validated, and run locally by the author.
