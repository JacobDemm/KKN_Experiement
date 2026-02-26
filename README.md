# K-Nearest Neighbor Experiment

## Overview

This project recreates the graphs from **Slides 27–30** of Chapter 2 using custom Gaussian mixture distributions and a K-Nearest Neighbours (KNN) classifier in 2D.

---

## Data Generation

Each class is sampled from a mixture of Gaussian components using custom center arrays and spread values.

- **Centers:** Real-valued coordinates ranging from **-2.5 to 1.5** for both Class 0 and Class 1
- **Class 0 spread:** `sigma = 0.27` → tighter, more compact blobs
- **Class 1 spread:** `sigma = 0.63` → wider, more spread out blobs

The asymmetric sigmas create a unique and realistic decision boundary where the two classes have different levels of spread.

---

## Results

### Best K = 2 (Optimal Fit)
- **Train Accuracy:** 92.9% (Train Error: 0.071)
- **Test Accuracy:** 93.3% (Test Error: 0.067)
- The KNN boundary closely follows the Bayes-optimal boundary

### K = 1 (Overfitting — High Variance)
- **Train Accuracy:** 100%
- **Test Accuracy:** 88.9%
- The model memorises every training point, producing a jagged boundary that does not generalise well

### K = 100 (Underfitting — High Bias)
- **Train Accuracy:** < 50%
- **Test Accuracy:** < 50%
- Averaging too many neighbours produces an oversimplified boundary that fails to capture the true structure of the data

---

## Plots

| Plot | Description |
|------|-------------|
| **1** | Optimal (Bayes-proxy) decision boundary |
| **2** | Train & Test error rate vs 1/K — shows the U-shape and best K |
| **3** | K=1 overfitting — jagged boundary, high variance |
| **4** | K=100 underfitting — oversimplified boundary, high bias |

---

## Key Takeaways

- Changing the Gaussian centers and sigma values produces very different decision boundaries — some quite unusual in shape
- The **bias-variance trade-off** is clearly visible in the error vs 1/K plot: as K increases, variance decreases but bias increases
- The optimal K minimises test error, balancing both
- A model with 100% training accuracy (K=1) is not necessarily the best — it overfits the training noise
