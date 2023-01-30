---
title: Dataset Augmentation in Feature Space
authors: Terrance DeVries, Graham W. Taylor
year: 2017
---

#computer-vision #data-augmentation 

## TLDR;
Data augmentation is domain-dependent and sometimes need adequate expertise to truly benefit from it. So, the paper proposes a domain-independent data augmentation procedure that interpolates and extrapolates between samples direcly in the feature space.

## Problem Indentified
- Data augmentation is a very important process to expand trainngin data
- However, augmentation operations are domain-agnostic, may need careful expertise or trial-error to be used correctly.

## Solution proposed 
- Augmenting the data in the feature space instead of the input space by interpolating and extrapoling vectors in the embedding space.
- This creates an augmentation operation that does not depend on the input space and is therefore domain agnostic.

## Contributions
- The paper proposes a model-agnostic data augmentation method.

## Methodology
- An autoencoder is first trained to permit use to get context vector that we can manipulate
- From the representations obtained from the autoencoder, we can perform three data augmentations procedure.
	- Noising
	- Interpolation
	- Extrapolation
- After the data augmentation on the feature space, we can use the augmented samples to train a decoder or sequence classifier.
- The autoencoder is an LSTM neural network.

## Findings
- Surprisingly, extrapolation outperforms simple augmentation stratege on the **Arabic Digits dataset**, **CIFA10**, **MNIST**.

## Limitations
- The method has only been tested is relatively simple domains (maybe not **CIFAR10**)
- The augmented embeddings might not lead to true reconstruction of the samples as this is also depended of the encoder architecture used to get these embeddings.

## Improvements (sort of)
- Make the embeddings augmentation learnable through the encoder like [[@wilesCompressedVisionEfficient2022]]

## Cross-Reference
- 
