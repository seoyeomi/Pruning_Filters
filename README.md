# Pruning_Filters

## 1. Introduction
### 1.1 Background and Motivation
* The increasing size and complexity of deep learning models have made their deployment on resource-constrained environments, such as mobile and embedded systems, challenging.  
* Structured Pruning has emerged as an effective model compression technique, enabling significant reductions in model size and computational cost while maintaining competitive accuracy.  
* The seminal ICLR 2017 paper "Pruning Filters for Efficient ConvNets" introduced a method to prune filters based on L1-norm importance, achieving efficient convolutional networks through a systematic filter removal process.  

### 1.2 Objectives
This study aims to:
* Reproduce and extend the structured pruning methodology proposed in ICLR 2017 using the LightweightVGG16 model on the CIFAR-10 dataset.  
* Analyze the impact of pruning on computational cost (FLOPs), parameter count, and accuracy.  
* Explore retraining as a means of recovering the accuracy of pruned models and propse an optimized lightweight version.  

-----

## 2. Related Works
* Structured Pruning: This technique removes entire filters, channels, or other model structures to reduce computational complexity without introducing irregularities in the model architecture.  
* L1-Norm Importance: The magnitude of filter weights is used as a proxy for their importance, allowing for systematic pruning.  
* ICLR 2017 Study: Importance evaluation → Pruning → Retraining. Demonstrated on datasets like CIFAR-10 and ImageNet with models such as VGG and ResNet.  

### key Contribution: 
Our work replicates and extends this methodology using LightweightVGG16, with a focus on detailed analysis of FLOPs, parameters, and accuracy changes across pruning ratios.

-----
