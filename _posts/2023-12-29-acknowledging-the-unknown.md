---
layout: post
title: "[SPML] Acknowledging the Unknown for Multi-label Learning with Single Positive Labels"
categories: SPML
---

## **Related works**
SPML is related to multi-label learning with weak supervision, the following are two similar tasks and how they have been tackled:
- Multi-label learning with missing labels (MLML), where each training image is partially labeled, i.e for some classes, we don\'t know whether they are positives or negatives: treating missing labels as negative ones, label matrix completion, learning image-label similarities.
- Semi-supervised multi-label learning (SSML), where some images are fully annotated while the others are unlabeled: non-negative matrix factorization, label propagation, aligning image features. 

However, we can not directly apply these approaches to SPML setting, since each sample contains only one positive label.

Tools/topics used to build the proposed approach are **Entropy Min-/Maximization** and **Pseudo-labeling**.

### **Entropy Min-/Maximization**
It deserves another post (coming soon).
### **Pseudo-labeling (PL)**
Methods to implement PL includes exploiting neighborhood graphs, performing clustering, estimating prediction uncertainty. \
However, they all fail due to the positive-negative imbalance in SPML. Therefore, the proposed method follows **asymmetric-tolerance** strategies for positive and negative pseudo-labels.
