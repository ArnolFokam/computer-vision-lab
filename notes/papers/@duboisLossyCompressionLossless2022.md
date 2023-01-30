---
title: Lossy Compression for Lossless Prediction
authors: Yann Dubois, Benjamin Bloem-Reddy, Karen Ullrich, Chris J. Maddison
year: 2022
---

#representation-learning #contrastive-learning #generative-modelling #self-supervised-learning 

## TLDR;
This paper proposes new compression objectives to train neural compressors that provides considerable bit-rate gains while yeilding negligible to no loss in predictive performance compared to other compression mechanisms (JPEG, PNG etc). This paper also shows that SSL discriminative objectives are better objective for neural compressors if we wish to preserve classification accuracy.

## Problem Indentified
- Data in the *Deep Learning* era is required in huge quantity of data.
- As a result, we sometimes need to compress this data.
- Existing lossy compression retain image information useful for human perception but not forcefully for algorithm performance.
- As a result, we might have more information than what is needed for our model to perform its task.

## Solution proposed 
- This paper primarily propose new compression objectives for downstream tasks that trains neural compressors in a self-supervised learning setting.

## Contributions
- Provides a way to quantity the bit-rate of data to provide high performance models
- Build SSL objectives to train neural compressors for optimal bit-rate
- Build nerual compressors competitve to other compression techniques like JPEG.

## Methodology
- The paper attempts two moves
	1. Quantify bit-rate's relationship with downstream task performance.
	2. Creates self-supervised objectives leveraging  1 to learn how to compress data.
- The paper establishes a linear relationship between the log-loss decrease (compared to when we have the uncompressed data) and the bits saved (new free storage when saving the compressed representation instead)
- The paper chooses reconstruction of information about original data from distorted (compression) data as suitable objective to train neural compressors. Reconstruction can be formulated in two ways:
	- Reconstruct the original image (generative modelling)
		- Use a variational autoencoder to reconstruct the original sample from the augmented sample
	- Reconstruct enough information for classification (discriminative modelling)
		- Use Noise Contrastive Estimation loss function to ensure that predictions of the original samples matches does of the augmented samples.
- In addition to the above objective, the method adds an entropy bottleneck on the obtained representation to both objectives.  This bottleneck is supposed to ensure we keep the relavent information for invariant tasks.
- This bottleneck ensures lossless data compression through an entropy coding objective.

## Findings
- The choice of augmentation chosen affects the compression performance because choosing augmentation operations is equivalent to choosing the information we want to discard from the data.
- The BINCE (discrimanative) acheives better bit-rate gains then standard lossy and lossless compression mechanism (JPEG, PNG) with no impact on prediction performance.
- pretrained SSL can be used as generic compressor

## Limitations
**DISCLAIMER:** Not completely sure I understand the entire paper.
- The augmentation oeprations chosen influences the information preserved by the neural compressor. (limitation that arises from most SSL pretrain objectives relying on data augmentation)

## Improvements (sort of)
**DISCLAIMER:** Not completely sure I understand the entire paper.


## Cross-Reference
- 


