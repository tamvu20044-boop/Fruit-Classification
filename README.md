# 🍎 Fruit Classification: Transfer Learning vs. Custom CNN

An end-to-end deep learning benchmark comparing a custom-engineered **CNN from Scratch** against a fine-tuned **ConvNeXt-Tiny (Transfer Learning)** model for high-precision fruit classification.

---

## 🔬 Methodology & Experimental Results

To comprehensively evaluate model performance and representation learning capabilities, two distinct deep learning strategies were implemented and benchmarked on the test dataset:

---

### 1. Architectural Comparison

| Metric / Aspect | 🧱 Custom CNN (From Scratch) | 🚀 ConvNeXt-Tiny (Transfer Learning) |
| :--- | :--- | :--- |
| **Architecture** | Custom Deep CNN (7×7 Input Conv, BatchNorm, MaxPool & Dropout) | Modern **ConvNeXt-Tiny** Backbone |
| **Weights Initialization** | Random Initialization (Trained from scratch) | Pre-trained on **ImageNet-1K** |
| **Primary Objective** | Evaluate direct spatial feature extraction from domain data | Leverage pre-trained hierarchical representations with fine-tuning |
| **Top-1 Test Accuracy** | **59,84%** | **85,79%** *(+25,95% improvement)* |

---

### 2. Performance Insights & Key Takeaways

* **Custom CNN from Scratch (`59,84%`)**:
  * Successfully learned fundamental low-level filters (edges, textures, color gradients) directly from raw images.
  * Demonstrates solid baseline performance, but exhibits limited generalization capacity when distinguishing between visually ambiguous classes or items with varying illumination and occlusion.

* **ConvNeXt Transfer Learning (`85,79%`)**:
  * Outperformed the baseline by a large margin (**+25,95%**), capitalizing on rich semantic priors acquired from pre-training on millions of natural images.
  * Achieved significantly faster convergence, lower training loss variance, and well-calibrated confidence scores across all fruit categories.

---

### 3. Confusion Matrix Analysis

A side-by-side breakdown of classification predictions on the unseen test dataset:

| 🚀 ConvNeXt Transfer Learning (85,79%) | 🧱 Custom CNN from Scratch (59,84%) |
| :---: | :---: |
| ![ConvNeXt Confusion Matrix](convnext_transfer_learning/confusion_matrix.png) | ![Custom CNN Confusion Matrix](cnn_from_scratch/confusion_matrix.png) |
| *High concentration along the main diagonal indicating robust per-class precision.* | *Higher off-diagonal dispersion caused by inter-class visual similarities.* |
