---
title: Compressed Vision for Efficient Video Understanding
authors: Olivia Wiles, Joao Carreira, Iain Barr, Andrew Zisserman, Mateusz Malinowski
year: 2022
---

#computer-vision #video #compression #representation-learning #data-augmentation

## TLDR;
- We can approximate augmentation operations using neural networks and use them to train compressed video sequences.

## Problem Indentified
- Reasoning and Understanding is often temporal.
- Most computer vision research mostly focus on single images or short video sequence due to computational requirements of processing larger inputs
- Therefore, we need to devise a method that permits us to work with these longer sequences without drastically increasing our computational needs.

## Solution proposed 
- We can compress long videos into latent representations and directly work with these representations without needing any decompression mechanism.

## Contributions
- A **neural compression mechanism** that operators without the need of decompressing the the original (compressed) inputs for training.
- An **augmentation network** (learnable) that directly operates on the compressed latent representation.

## Methodology
- Neural Compression
	- An auto-encoder (VQ-VAE) network with $l_1$ reconstruction loss is used.
- Augmentation Network  $a(.)$ consist of:
	- a multi-layer  perceptron (MLP) which recieves the as input a tensor representing the transform.
	- A transformer that receives the concatenation of the MLP's output and input video latent representation and outputs the augmented latent representation.
	- A reconstruction loss $l_1$ is computed between the output of the transformer and the output of the *encoder* (VQ-VAE) when a standard augmentation operaiton is used.

## Findings
- The method is more effiecent than standard compression algorithm as we increase the compression rate.

## Limitations
- We need to reconstruct the video from the latent representation to train the augmentation network.

## Improvements (sort of)
- Directly working in the latent space  to train the augmentation network might be a nice follow-up direction. It would be interesting to replace the VQ-VAE with a self-supervised model then, train the augmentation network to output latent representations that are closer (in the latent space) to the representation obtained from the transformed video sequence rather than using  a reconstruction loss. Therefore, we could check if this matches with the representations obtained when we use an $l1$ loss. 

## Cross-Reference
- This work tries to augment data diretly in the latent space as in [[@devriesDatasetAugmentationFeature2017]]
- This work claims making representation invariant to all transformations without prior knowledge of the downstream tasks (as in [[@duboisLossyCompressionLossless2022]]) **might be detrimental** in for some tasks.
 
