---
title: Big Self-Supervised Models are Strong Semi-Supervised Learners
authors: Ting Chen, Simon Kornblith, Kevin Swersky, Mohammad Norouzi, Geoffrey Hinton
year: 2020
---

#representation-learning #contrastive-learning  #semi-supervised-learning

## TLDR;

The paper propose an emperically study of the inlfuence of bigger/deeper model on semi-supervised learning while proposing a framewark to leverage unlabelled data during the fine-tuning stage for extra performance boost compared to just using the pre-trained SSL model.

## Problem Indentified
- Self-supervised lerning's paradigm is great.
- Why not use this paradigm in semi-supervised learning?

## Solution proposed 
- A semi-supervised learning framework made up of:
	1. Self-supervised pre-training with unlabelled data (task-agnostic way)
	2. Supervised fine-tuning with small labelled data
	3. Self-training with unlabelled data

## Contributions
- Emperically study the influence of 
	- Model size
	- Projection Head
 on model performance in contrastive self-supervised learning
 - Shows the importance of leveraging unlabelled data during fine-tuning to get extra perf improvements.

## Methodology
- Use the same SimCLR framework proposed by [[@chenSimpleFrameworkContrastive2020]] but
	- With deeper models (ResNet50 => ResNet152)
	- Deeper projection head and fine-tuning of one its layers (not completely removed as in the past)
	- Adds a memory network to get more negative examples
	for self-supervised pretraining and fine-tuning.
- Then, we use the pre-trained network to impute labels on a large unlaballed set to train a student network through self-distillation
- During this process, we train the student network to have matching predictions with the teacher network.

## Findings
- Bigger models are more label-effiecient
- Bigger/Deeper projection heads improve representation learning
- Self-distillition improves semi-supervised learning when the student network has both the same  or different arch as the teacher model.

## Limitations
- Only ImageNet used
- Same dataset from pre-training used during self-distillation. Aren't we overfiiting to particular data distribution overfitting?

## Improvements (sort of)
- Evaluate performance on more datasets
- What would happen if use a different unlabelled set during finetuning (synthetic image for example)

## Cross-Reference
- The paper uses the framework proposed by [[@chenSimpleFrameworkContrastive2020]]

