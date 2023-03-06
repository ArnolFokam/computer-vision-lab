---
title: Directional Self-supervised Learning for Heavy Image Augmentations
authors: Yalong Bai, Yifan Yang, Wei Zhang, Tao Mei
year: 2021
---

#representation-learning #contrastive-learning #data-augmentation #self-supervised-learning 

## TLDR;
This paper proposes a new self-supervised learning training paradigm that leverages heavy data augmentation in a novel way to prevent collapse in non-contrastive SSL objectives and improve perfromance. This paradigm maximises mutual infromation between heavily augmented views and thier source while still maximizing the MI between the lightly augmented views.

## Problem Indentified
- Self-Supervised Learning is great!
- It depends on the careful selection of augmentation policies that can make self-supervised learning very good
- However, using other heavy augmentation is detrimental to the performance of non-contrastive SSL methods
- This is can even lead to a collapse in the performance of SSL models.

## Solution proposed 
- A SSL objective function that can leverage heavier augmentation operation without collapse on non-contrastive objective like SimSiam.

## Contributions
- New objective function that works with heavy data augemtation

## Methodology
- We provide two views from an anchor image usign light augmentations
- From each view, we provide two views from heavy augmentations
- We have two objective functions
	- The first one maximizes MI between different augmentation  from light augmented images (symmetric loss)
	- The second maximizes MI between the heavily augmented views and their source (assymmetric loss)

## Findings
- Heavy augmentations make non-contrastive objective SimSiam collapse
- Performs better than the current baseline even for contrastive methods

## Limitations
- 

## Improvements (sort of)
- 

## Cross-Reference
- 
