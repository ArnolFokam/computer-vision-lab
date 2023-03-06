---
title: Rethinking Rotation in Self-Supervised Contrastive Learning: Adaptive Positive or Negative Data Augmentation
authors: Atsuyuki Miyai, Qing Yu, Daiki Ikami, Go Irie, Kiyoharu Aizawa
year: 2022
---
#representation-learning #contrastive-learning #data-augmentation #self-supervised-learning 

## TLDR;
This paper proposes a solution to the detrimental effects of rotation transforms on self-supervised learning. It proposes a way to identify rotation agnostic and non-agnostic views using entropy-based models. Then, attract samples from rotation agnostic and repel the ones from non-rotation agnostic views.

## Problem Indentified
- Rotation is detrimental the performance of self-supervised learning
- The authors claim this is because of the incentive of the original contrastive learning framework to treat all transformed images as positive no matter the amount of semantical content they have.

## Solution proposed 
- This paper proposes an approach that looks at the semantic content of images before deciding whether the rotated images should be treated as positive or negative.

## Contributions
- A novel contrastive framework based on image semantic

## Methodology
- Sample rotation-agnostic images from the unlabelled dataset in an unsupervised way
	- We have a rotation predictor model that classify rotated images between different rotation labels
	- An additional objective function of this model is to increate the enrtopy of predictions with already decently high entropies. (predictions assumed to be from RAI agnostic images) - **not confident about this, check again the paper later**
- Maximize the similarity between sampled rotation-agnostic image and minimize the similarity between the rest (non rotation-agnostice images)

## Findings
- The paper makes a good point into claiming though rotation large affects the image semantics and can be therefore detrimental to self-supervised learning, we can improve the training strategy to take into account the semantics of the image when doing data augmention

## Limitations
- Might need explanations as to why the entropy loss functions
	- Urges to model to rotation predictor model to be confident in non-RAI images and be inaccurate for the RAI.
	- Why is that a wanted behaviour?
- Introduces another hyperparameter

## Improvements (sort of)
- Would be nice to have a semantic base approach to self-supervised learning data augmentation.

## Cross-Reference
- Attempts a modification of the augmentation module in contrastive learning as [[@zhangRethinkingAugmentationModule2022]]
- It also has a semantic-based approach self-supervised data augmentation as [[@pengCraftingBetterContrastive2022]]
