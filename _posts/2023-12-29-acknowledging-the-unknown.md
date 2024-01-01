---
layout: post
title: "[SPML] Acknowledging the Unknown for Multi-label Learning with Single Positive Labels"
categories: SPML
---

## **Related works**
Single Positive Multi-label Learning (SPML) is related to multi-label learning with weak supervision, the following are two similar tasks and how they have been tackled:
- Multi-label learning with missing labels (MLML), where each training image is partially labeled, i.e for some classes, we don\'t know whether they are positives or negatives: treating missing labels as negative ones, label matrix completion, learning image-label similarities.
- Semi-supervised multi-label learning (SSML), where some images are fully annotated while the others are unlabeled: non-negative matrix factorization, label propagation, aligning image features. 

However, we can not directly apply these approaches to SPML setting, since each sample contains only one positive label.

Tools/topics used to build the proposed approach are **Entropy Min-/Maximization** and **Pseudo-labeling**.

### **Entropy Min-/Maximization**
It deserves another post (coming soon).
### **Pseudo-labeling (PL)**
Methods to implement PL includes exploiting neighborhood graphs, performing clustering, estimating prediction uncertainty. \
However, they all fail due to the positive-negative imbalance in SPML. Therefore, the proposed method follows **asymmetric-tolerance** strategies for positive and negative pseudo-labels.

## **Proposed method**
### **Problem definition**
Let $$\mathcal{D} = \{(\mathrm{x}^{(n)}, \mathrm{y}^{(n)})\}_{n=1}^N$$ denotes a partially labeled multi-label dataset with $$N$$ images, where each input image $$\mathrm{x}^{(n)}$$ from input space $$\mathcal{X}$$ is associated with a vector of label $$\mathrm{y}$$ from the space $$\mathcal{Y} = \{0,1\}^C$$ with $$C$$ classes. Let $$y_c^{(n)}$$ be the $$c$$-th entry of $$\mathrm{y}^{(n)}$$, where $$y_c^{(n) = 1}$$ indicates $$\mathrm{x^{(n)}}$$ contains a positive label of the $$c$$-th class, whereas $$y_c^{(n)} = 0$$ indicates that the label of the $$c$$-th class is unannotated for $$\mathrm{x}^{(n)}$$. In SPML, only one positive label is annotated for each training image. \


## **What I\'ve learned from this paper**
- Entropy min-/maximization
- Gradient-based analysis for studying loss functions

## **References**