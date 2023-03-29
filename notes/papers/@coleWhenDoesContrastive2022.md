---
title: When Does Contrastive Visual Representation Learning Work?
authors: Elijah Cole, Xuan Yang, Kimberly Wilber, Oisin Mac Aodha, Serge Belongie
year: 2022
---

## TLDR;
- This paper provides a comprehensive study of self-supervised learning and how its performance is affected by different properties of differents datasets.

## Problem Indentified
- Self-supervised learning is closing closed the gap with supervised learning
- However, its study is done mainly on one dataset and therefore, we have little knowledge on the performance of such techniques for other datasets.
- We also do not what are  the factors that needs to be considered when applying such techniques in other datasets.

## Solution proposed 
- The paper proposes of analytical study of all the components of SSL and how it affects data with different characteristics.

## Contributions
- Analytic study of the effects of dataset on SSL
- A list of recommendataions when using SSL in datasets different from ImageNet

## Methodology
- The paper performs experiments on four large-scale datasets
	- ImageNet 
	- iNat21
	- Places365 
	- GLC20
- These datasets have the same size
- The choice is because these dataset spans various properties accross a spectrum of them
	- Curated vs In the wild
	- fine vs coarse-grained
	- object-centric vs scenes
#### Experiments
- For pretraining, the size of the pretrain data is varied 
- The models used are SimCLR, MoCo and BYOL

## Findings

#### Data Quantity
- There is little benefit beyond 500k pretraining images
- Although self-supervised leanring works well, we remark for these datsets need quit a fair amount of lable to brigde between it supervised leaning.
- 
#### Data Domain
- in-domain performance outperform cross-domain performance
- Combining dataset does not usually gives the expected increase in cross-domain performance
- Combinine self-supervised and supervised represenatations improves performance significantly

#### Data quality
- Self-supervised learning is more affected by image corruption on the pre-training data compare to supervised with corruption on the training data.
- Image resolution is critical to SSL. They are more affected by image downsampling than by salt and pepper noise.

#### Task granularity
- SSL may fail to capture fine-grained semantic information as effectively as supervised learning.

## Limitations
- 

## Improvements (sort of)
- 

## Cross-Reference
- 
