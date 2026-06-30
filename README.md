# Redrob AI Candidate Ranker

## Overview

This project was developed for the **Redrob Data & AI Challenge**.

The objective is to build an intelligent candidate discovery system capable of ranking candidates beyond simple keyword matching by combining structured profile features, behavioral signals, and semantic similarity.

The solution is designed to efficiently process large candidate datasets and generate an explainable ranked shortlist suitable for recruiter workflows.

---

## Problem Statement

Traditional recruitment systems rely heavily on keyword matching, often overlooking qualified candidates whose experience is expressed differently.

This project addresses that limitation by combining:

- Feature-based candidate scoring
- Semantic profile understanding
- Behavioral signals
- Explainable AI ranking

to recommend the most relevant candidates for a given job description.

---

# Solution Architecture

```
                     Job Description
                             │
                             ▼
                Job Description Parsing
                             │
                             ▼
          Feature-Based Candidate Scoring
               (100,000 Candidate Profiles)
                             │
                             ▼
               Top Candidate Preselection
                             │
                             ▼
        Semantic Embedding using BGE Model
                             │
                             ▼
          Cosine Similarity Re-ranking
                             │
                             ▼
             Final Weighted Candidate Rank
                             │
                             ▼
                  submission.csv
```

---

# Methodology

The ranking system follows a two-stage retrieval architecture.

## Stage 1 – Feature-Based Retrieval

Each candidate profile is evaluated using structured profile information including:

- Technical skills
- Current role
- Career history
- Years of experience
- Production AI indicators
- Behavioral signals

A weighted scoring function identifies the most relevant candidates while efficiently filtering the dataset.

---

## Stage 2 – Semantic Re-ranking

The shortlisted candidates are embedded using:

**BAAI/bge-small-en-v1.5**

The system generates semantic embeddings for both:

- Job Description
- Candidate Profile

Cosine similarity is then used to estimate contextual relevance between the job requirements and each candidate profile.

---

## Final Ranking

The final candidate score combines:

- Feature-based retrieval score
- Semantic similarity score

The highest-ranked candidates are exported with explainable reasoning describing why each candidate was selected.

---

# Features Used

## Candidate Features

- Current job title
- Professional summary
- Technical skills
- Career history
- Years of experience

## Behavioral Signals

- Recruiter response rate
- Interview completion rate
- GitHub activity
- Open-to-work status
- Notice period

## Semantic Features

- Job description embeddings
- Candidate profile embeddings
- Cosine similarity

---

# Technologies

- Python
- Sentence Transformers
- BAAI/bge-small-en-v1.5
- NumPy
- Pandas
- Scikit-learn
- python-docx
- tqdm

---

# Repository Structure

```
Redrob-AI-Candidate-Ranker/

├── Candidate_Ranker.ipynb
├── README.md
├── requirements.txt
├── LICENSE
│
└── outputs/
    └── submission.csv
```

---

# Installation

Install the required packages:

```bash
pip install -r requirements.txt
```

---

# Required Input Files

The notebook expects the following input files:

- `candidates.jsonl`
- `job_description.docx`

These files are provided as part of the challenge dataset and are **not included** in this repository.

---

# Running the Project

Run the notebook:

```
Candidate_Ranker.ipynb
```

The notebook performs:

1. Job description parsing
2. Feature-based candidate scoring
3. Candidate preselection
4. Semantic embedding
5. Final ranking
6. Submission generation

The final output is:

```
submission.csv
```

---

# Output Format

The generated submission contains:

| Column | Description |
|---------|-------------|
| candidate_id | Candidate identifier |
| rank | Final ranking |
| score | Final ranking score |
| reasoning | Explainable recommendation |

---

# Performance

The proposed pipeline:

- Processes over **100,000 candidate profiles**
- Uses efficient streaming to reduce memory usage
- Applies two-stage retrieval for scalability
- Produces explainable candidate recommendations
- Performs semantic matching beyond keyword search

---

# Future Improvements

Potential future enhancements include:

- Cross-Encoder re-ranking
- Hybrid lexical + semantic retrieval
- Learning-to-Rank optimization
- Hyperparameter tuning
- GPU acceleration for large-scale inference

---

# License

This project is released under the MIT License.

---

# Author

Developed for the **Redrob Data & AI Challenge**.
