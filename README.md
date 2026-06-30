# Redrob AI Candidate Ranker

## Overview

This project was developed for the **Redrob Data & AI Challenge**. It presents an AI-powered candidate discovery system that ranks candidates using a combination of structured profile features, behavioral signals, and semantic similarity.

Unlike traditional keyword-based search, the system performs contextual matching between job descriptions and candidate profiles to identify the most relevant candidates and generate an explainable ranked shortlist.

---

## Problem Statement

Recruiters often rely on keyword matching to search candidate profiles. This approach can overlook highly qualified candidates whose experience and skills are expressed differently.

The objective of this project is to build an intelligent ranking system capable of:

- Understanding complex job descriptions
- Identifying semantically relevant candidates
- Incorporating behavioral and profile signals
- Producing an accurate ranked shortlist with explainable reasoning

---

## Solution Architecture

```
                 Job Description
                        │
                        ▼
           Job Requirement Extraction
                        │
                        ▼
         Feature-Based Candidate Scoring
                (100,000 Candidates)
                        │
                        ▼
             Top Candidate Selection
                        │
                        ▼
        Semantic Embedding Re-ranking
        (BAAI/bge-small-en-v1.5)
                        │
                        ▼
            Final Candidate Ranking
                        │
                        ▼
                submission.csv
```

---

## Methodology

### 1. Job Description Processing

The system extracts important technical and domain-specific requirements from the supplied job description, including:

- AI and Machine Learning technologies
- Vector databases
- Search and retrieval concepts
- LLM-related skills
- Soft skills

---

### 2. Feature-Based Candidate Retrieval

Each candidate profile is evaluated using structured features such as:

- Technical skills
- Years of experience
- Current job title
- Production AI experience
- Behavioral signals

Only the highest scoring candidates proceed to the semantic ranking stage.

---

### 3. Semantic Re-ranking

Candidate profiles are converted into semantic representations using:

**BAAI/bge-small-en-v1.5**

Cosine similarity is computed between the job description embedding and candidate embeddings to estimate contextual relevance.

---

### 4. Final Ranking

The final ranking combines:

- Feature-based retrieval score
- Semantic similarity score

The top 100 candidates are exported together with explainable reasoning.

---

## Features Used

### Candidate Features

- Current role
- Professional summary
- Skills
- Career history
- Years of experience

### Behavioral Signals

- Recruiter response rate
- Interview completion rate
- GitHub activity
- Open-to-work status
- Notice period

### Semantic Features

- Job description embeddings
- Candidate profile embeddings
- Cosine similarity

---

## Technologies

- Python
- Sentence Transformers
- BAAI/bge-small-en-v1.5
- NumPy
- Pandas
- Scikit-learn
- python-docx
- tqdm

---

## Repository Structure

```
Redrob-AI-Candidate-Ranker/

├── Redrob_AI_Ranker.ipynb
├── README.md
├── requirements.txt
├── LICENSE
├── outputs/
│   └── submission.csv
└── docs/
```

---

## How to Run

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Required Input Files

Place the following files in the project directory:

- candidates.jsonl
- job_description.docx

### Run

Execute the notebook:

```
Redrob_AI_Ranker.ipynb
```

The notebook generates:

```
submission.csv
```

---

## Output

The generated submission file contains:

| Column | Description |
|---------|-------------|
| candidate_id | Candidate identifier |
| rank | Final ranking position |
| score | Combined ranking score |
| reasoning | Explanation of why the candidate was selected |

---

## Results

The proposed system:

- Processes over 100,000 candidate profiles
- Uses a two-stage retrieval pipeline for efficient ranking
- Performs semantic matching beyond keyword search
- Incorporates behavioral signals into ranking
- Produces explainable recommendations suitable for recruiter review

---

## Future Improvements

Potential enhancements include:

- Cross-Encoder re-ranking
- Hybrid BM25 + semantic retrieval
- Learning-to-Rank models
- GPU acceleration
- Automated hyperparameter tuning

---

## Author

Developed for the **Redrob Data & AI Challenge**.
