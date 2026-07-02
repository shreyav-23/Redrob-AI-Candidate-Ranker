# Redrob AI Talent Ranking Challenge

## Overview

This repository contains our solution for the **Redrob AI Talent Ranking Challenge**.

The objective of the challenge is to identify and rank the **top 100 candidates** from the provided candidate dataset for the released job description.

To address this, we built a **two-stage hybrid ranking pipeline** that combines structured candidate scoring with semantic similarity matching. The system is designed to efficiently identify high-quality candidates while remaining compatible with the competition’s **CPU-only runtime constraints**.

Instead of relying only on keyword matching, the pipeline incorporates multiple signals, including:

* **Feature-based candidate scoring**
* **Profile consistency checks**
* **Behavioral hiring indicators**
* **Semantic candidate–job matching**
* **Explainable candidate ranking**

---

## Output

The ranking pipeline generates the final submission file:

```text id="hkpib9"
P_for_Positive.csv
```

---

## Running the Project in Google Colab

This project is designed to be executed in Google Colab using the provided notebook.

1. Upload the required input files
Upload the following files to your Colab session:
candidates.jsonl
job_description.docx

2. Open the notebook
Open ranking.ipynb in Google Colab.

3. Run all notebook cells in order
Run the notebook from top to bottom. The notebook includes a dependency installation cell, so no separate environment setup is required outside the notebook.

4. Generate the submission file
After all cells have run successfully, the final submission file will be generated as:
P_for_Positive.csv

---

## Notes

* Make sure `candidates.jsonl` and `job_description.docx` are available in the Colab runtime before running the notebook.
* The final ranking and reasoning output are generated entirely from the uploaded candidate dataset and job description.
