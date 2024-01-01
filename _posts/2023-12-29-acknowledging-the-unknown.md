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
Let $$\mathcal{D} = \{(\mathrm{x}^{(n)}, \mathrm{y}^{(n)})\}_{n=1}^N$$ denotes a partially labeled multi-label dataset with $$N$$ images, where each input image $$\mathrm{x}^{(n)}$$ from input space $$\mathcal{X}$$ is associated with a vector of label $$\mathrm{y}$$ from the space $$\mathcal{Y} = \{0,1\}^C$$ with $$C$$ classes. Let $$y_c^{(n)}$$ be the $$c$$-th entry of $$\mathrm{y}^{(n)}$$, where $$y_c^{(n)} = 1$$ indicates $$\mathrm{x^{(n)}}$$ contains a positive label of the $$c$$-th class, whereas $$y_c^{(n)} = 0$$ indicates that the label of the $$c$$-th class is unannotated for $$\mathrm{x}^{(n)}$$. In SPML, only one positive label is annotated for each training image. \

### **Entropy-Maximization Loss**
If we assume all the unannotated labels are negative ones, the $$\textit{assuming-negative}$$ (AN) loss is defined as:
$$
\begin{align}
    \mathcal{L}_{\mathrm{AN}}(\mathrm{f}^{(n)}, \mathrm{y}^{(n)}) = -\frac{1}{C}\sum_{c=1}^{C}[\mathbf{1}_{[y_c^{(n)}=1]}\mathrm{log}(f_c^{(n)})+\mathbf{1}_{[y_c^{(n)}=0]}\mathrm{log}(1-f_c^{(n)})]
\end{align}
$$
Since this assumption is unrealistic and thus can hurt model generalization. The paper treats these unannotated labels as unknown and propose $$\textit{entropy-maximization (EM) loss}$$ for SPML as follows:
$$
\begin{align}
    \mathcal{L}_{\mathrm{EM}}(\mathrm{f}^{(n)}, \mathrm{y}^{(n)}) = -\frac{1}{C}\sum_{c=1}^{C}[\mathbf{1}_{[y_c^{(n)}=1]}\mathrm{log}(f_c^{(n)})+\mathbf{1}_{[y_c^{(n)}=0]}\alpha H(f_c^{(n)})], \\
    H(f_c^{(n)})=-[f_c^{(n)}\mathrm{log}(f_c^{(n)}) + (1-f_c^{(n)})\mathrm{log}(1-f_c^{(n)})]
\end{align}
$$

Here $$H(f_c^{(n)})$$ is the Shannon entropy of the predicted probabilities for the unannotated labels. Let $$i$$ be the annotated positive class and $$j$$ denote the unknown classes, the $$\textit{EM loss}$$ can be rewritten as: 
$$
\begin{align*}
    \mathcal{L}_{\mathrm{EM}}(\mathrm{f}^{(n)}, \mathrm{y}^{(n)}) = -\frac{1}{C}\mathrm{log}(f_i^{(n)})-\frac{\alpha}{C}\sum_{1 \leq j \leq C}^{j \neq i}H(f_j^{(n)})
\end{align*}
$$

Note that by minimizing $$-H(f_j^{(n)})$$, we are indirectly maximizing the entropy itself. **The intuition is, since we know nothing about the true labels of the unannotated classes, we are not sure how should our predicted probabilities should be optimized to, so the best thing to do in this situation is to be a bit "conservative", or as least biased as possible.** 
## **What I\'ve learned from this paper**
- Entropy min-/maximization
- Gradient-based analysis for studying loss functions

## **References**