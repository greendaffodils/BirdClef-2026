# BirdCLEF+ 2026 Bronze Medal Solution

## Overview

This repository contains my solution for the Kaggle BirdCLEF+ 2026 competition, a large-scale bioacoustic species classification challenge involving weakly-labeled soundscape recordings across 234 species.

**Result**

* Private Leaderboard Macro ROC-AUC: **0.94221**
* Bronze Medal
* Global Rank: **294 / 4244**

---

## Solution Architecture

The final solution combines two complementary branches:

### 1. Perch + ProtoSSM Branch

* Pretrained Perch v1 embeddings extracted from 5-second soundscape windows
* ProtoSSM sequence model for temporal context modeling
* MLP probes trained on Perch embeddings and classifier scores
* ResidualSSM correction model for sequence-level refinement

Public Leaderboard Score:

* **0.928**

---

### 2. SED Branch

* Mel-spectrogram based audio representation
* Distilled Sound Event Detection (SED) model
* EfficientNet-B0 backbone
* BCE loss for multi-label classification

Public Leaderboard Score:

* **0.949**

---

## Ensemble

The final prediction combines both branches through:

* Rank-based fusion
* Power Optimization for weight selection
* Taxonomy-aware ranking
* Residual sequence correction

This ensemble consistently outperformed individual models on validation and leaderboard data.

---

## Training Pipeline

### Feature Extraction

* Perch v1 embeddings
* Mel Spectrograms

### Models

* EfficientNet-B0
* ProtoSSM
* ResidualSSM
* MLP Probes

### Loss Function

* Binary Cross Entropy (BCE)

### Evaluation Metric

* Macro ROC-AUC

---

## Key Techniques

* Weakly-supervised learning
* Temporal sequence modeling
* Multi-model ensembling
* Long-tail species handling
* False-positive reduction
* Residual correction networks

---

## Final Performance

| Model                           |          Public LB |
| ------------------------------- | -----------------: |
| Perch + ProtoSSM + ResidualSSM  |              0.928 |
| Distilled SED (EfficientNet-B0) |              0.949 |
| Final Ensemble                  | 0.94221 Private LB |

---

## Tech Stack

* Python
* PyTorch
* TensorFlow
* ONNX Runtime
* NumPy
* Pandas
* Scikit-Learn

---

## Acknowledgements

The solution builds upon publicly available BirdCLEF baselines, Perch embeddings, and community research shared throughout the competition.
