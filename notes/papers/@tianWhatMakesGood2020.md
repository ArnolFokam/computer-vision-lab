---
title: What Makes for Good Views for Contrastive Learning?
authors: Yonglong Tian, Chen Sun, Ben Poole, Dilip Krishnan, Cordelia Schmid, Phillip Isola
year: 2020
---

#representation-learning #self-supervised-learning #semi-supervised-learning 

## TLDR;
The paper hypothesis that we don't want to maximize the MI between views only as this may add irrelevant information of downstream tasks. Instead, it says we want to have a sweet spot in MI and to perform this devise new semi-supervised objective that use an adversarial augmentor to regulate the amount of MI that should be shared between views.

## Problem Indentified
- Learning good representation of the data is important
- In contrastive representation learning, the choice of views influence the performance of the representation obtained on downstream tasks
- However, little is known as to what makes good views for contrastive learning.

## Solution proposed 
- A semi-supervised objective to find the sweet spot in MI to share between views' representation.

## Contributions
- Demonstrate that good views for contrastive representation learning are those that shared the minimal task-relevant information between them
- Provides a new semi-supervised objective to get views that shares task-revelant information

## Methodology
- Construct a set of labelled and unlabelled data
- Pass the input image through a convolution piwel-wise image augmentor that acts as an adversarial augmentor.
- Therefore,
	- While the infoNCE aims at maximizing MI between views' representation
	- The adversarial augmentor aims to provide less and less MI in the views themselves
- A supervised objective ensures that we can still get enough information in the image to classify them.

## Findings
- Produces minimal gains compared to recent proposed SSL objectives

## Limitations
- It limits the application of infoNCE to semi-supervised objective
- It limits the type of augmentation to pixel-wise augmentation
- The paper proposes the use of RandAugment reduce the available MI between. This might be nice but  might as well remove the revelant MI from views.

## Improvements (sort of)
- Build a learnable strategy for other augmentations

## Cross-Reference
- 
