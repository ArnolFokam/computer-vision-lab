---
title: Debiased Contrastive Learning
authors: Ching-Yao Chuang, Joshua Robinson, Lin Yen-Chen, Antonio Torralba, Stefanie Jegelka
year: 2020
---

#representation-learning #contrastive-learning #self-supervised-learning 

## TLDR;
This paper proposes the use of novel contrastive loss for self-supervised learning such that the effect of the negative samples is re-weighted by adding a term that depends on additional positive samples in the denominator.

## Problem Indentified
- Self-supervised learning is great but there exists a sampling bias that make hard to get a perfect of true negative samples.

## Solution proposed 
- A contrastive loss function closer to ideal unbaised loss and more robust against the sampling bias of the origin contrastive loss function

## Contributions
- A new contrastive loss function robust against sampling bias in self-supervised contrastive learning.

## Methodology
- The paper designs a new loss function aroung the PU (Positive-Unlabelled) Learning framework.
- So instead of sampling from a margin distribution $p(x)$, we sample using the distribution
$$
p_x^{-}\left(x^{\prime}\right)=\left(p\left(x^{\prime}\right)-\tau^{+} p_x^{+}\left(x^{\prime}\right)\right) / \tau^{-}
$$

- This loss function does not treat samples from different images as negative samples but as unlabelled samples that needs to be discriminated from positive samples (according to PU learning).
- However, the effects of the bias is reduced through the addition of addititonal positive samples $v$.
$$
g\left(x,\left\{u_i\right\}_{i=1}^N,\left\{v_i\right\}_{i=1}^M\right)=\max \left\{\frac{1}{\tau^{-}}\left(\frac{1}{N} \sum_{i=1}^N e^{f(x)^T f\left(u_i\right)}-\tau^{+} \frac{1}{M} \sum_{i=1}^M e^{f(x)^T f\left(v_i\right)}\right), e^{-1 / t}\right\}
$$
With $N$ samples $\left\{u_i\right\}_{i=1}^N$ from $p$ (unlabelled set) and $M$ samples $\left\{v_i\right\}_{i=1}^M$ from $p_x^{+}$ (through data augmentation).

## Findings
- Positive examples does not have greater improvements as we increase its number
- Debiased loss with more positive examples leads to better seperation in class representations

## Limitations
- There is still additional bias introduced by the assumption of the marginal distribution of positive class $\tau^{+}$.
- The positives effects of debaising the losss diminishes with more negatives used

## Improvements (sort of)
- Re-weighting negatives samples indivudually instead of re-weighting the collective bias.

## Cross-Reference
- [[@robinsonContrastiveLearningHard2021]] designs a similar loss but in addition, reweights the samples based on thier similarity score with the anchor.+


