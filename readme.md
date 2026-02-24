# TOPSIS for Best Pre-trained SBERT Model Selection

##  Project Overview
This repository contains a Python implementation of the **TOPSIS** (Technique for Order of Preference by Similarity to Ideal Solution) algorithm. The goal is to determine the most well-rounded pre-trained **Sentence-BERT (SBERT)** model for text sentence similarity by balancing performance metrics against computational costs.

## Methodology
TOPSIS is a multi-criteria decision-making (MCDM) method that ranks alternatives by calculating their geometric distance from:
1.  **Positive Ideal Solution (PIS):** The hypothetical best possible values across all criteria.
2.  **Negative Ideal Solution (NIS):** The hypothetical worst possible values across all criteria.

Models that are closest to the PIS and farthest from the NIS receive the highest score.

##  Criteria and Weightage
The evaluation uses four key criteria, reflecting a balance between accuracy and production efficiency:

| Criterion | Type | Weight | Description |
| :--- | :--- | :--- | :--- |
| **Accuracy (STS)** | Benefit (+) | 0.40 | Performance on the Semantic Textual Similarity Benchmark. |
| **Inference Speed** | Benefit (+) | 0.30 | Throughput (Sentences processed per second). |
| **Model Size (MB)** | Cost (-) | 0.20 | Memory footprint on disk/RAM. |
| **Dimensions** | Cost (-) | 0.10 | Vector length (impacts storage & search speed). |

## Final Rankings
Based on the balanced weights, the models ranked as follows:

| Rank | Model | TOPSIS Score | Key Strength |
| :--- | :--- | :--- | :--- |
| **1** | `all-MiniLM-L6-v2` | **0.9236** | Extreme speed and tiny size. |
| **2** | `all-MiniLM-L12-v2` | **0.5477** | Excellent balance of quality/speed. |
| **3** | `paraphrase-albert-small-v2`| **0.4712** | Lowest memory footprint. |
| **4** | `all-distilroberta-v1` | **0.2312** | Moderate speed but high resource cost. |
| **5** | `all-mpnet-base-v2` | **0.1387** | High accuracy but extremely slow/heavy. |
