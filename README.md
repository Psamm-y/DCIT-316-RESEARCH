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
