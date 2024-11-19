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


## 2. Related Works
* Structured Pruning: This technique removes entire filters, channels, or other model structures to reduce computational complexity without introducing irregularities in the model architecture.  
* L1-Norm Importance: The magnitude of filter weights is used as a proxy for their importance, allowing for systematic pruning.  
* ICLR 2017 Study: Importance evaluation → Pruning → Retraining. Demonstrated on datasets like CIFAR-10 and ImageNet with models such as VGG and ResNet.  

### key Contribution: 
Our work replicates and extends this methodology using LightweightVGG16, with a focus on detailed analysis of FLOPs, parameters, and accuracy changes across pruning ratios.


## 3. Methodology
### 3.1 Experimental Setup
* Model : LightWeightVGG16
* Dataset : CIFAR-10 (10 classes, 32x32 resolution)
* Framework : PyTorch
* Metrics: FLOPs(measured using ptflops), Parameters(counted via PyTorch utilities), Accuracy(Top-1 Accuracy on the test set)

### 3.2 Pruning Workflow
1. Filter Importance Calculation:
   * The L1-norm of filter weights is computed to determine their relative importance.

2. Pruning Ratios:
   * Incrementally prune 10% to 90% of filters in steps of 10%.

4. Retraining:
   * Retrain pruned models for 1–5 epochs on CIFAR-10 using SGD optimizer and CrossEntropy loss.

5. Evaluation:
   * Compare pruned and retrained models in terms of FLOPs, parameter count, and accuracy.
  

## 4. Results and Analysis
### 4.1 Accuracy vs. Pruning Ratio
Results:
Layer-wise accuracy changes as pruning ratios increase, visualized through tables and graphs.

Observations:
Initial pruning (10%–30%) causes minor accuracy drops.
Significant degradation occurs beyond 50% pruning.

### 4.2 FLOPs and Parameter Count
Results:
Pre- and post-pruning comparisons of computational cost and model size.

Observations:
FLOPs and parameter counts decrease linearly with pruning ratio.
50% pruning achieves a balance between model size reduction and acceptable accuracy.


## 5. Conclustion and Future Work
### 5.1 Conclusion
* L1-norm based structured pruning was successfully implemented on LightweightVGG16.
* A 50% pruning ratio reduced FLOPs by ~50% (40.23 MMac) while maintaining acceptable accuracy (accuracy drop within 2%).
* Retraining proved effective in restoring accuracy, making pruned models viable for resource-constrained environments.

### 5.2 Future Work
* Extend experiments to larger datasets (e.g., ImageNet) and other architectures (e.g., ResNet, EfficientNet).
* Explore real-world deployment with hardware optimization.
* Investigate combinations of structured pruning with techniques like knowledge distillation.


## 6. References
* He, Y., Zhang, X., & Sun, J. (2017). "Pruning Filters for Efficient ConvNets." International Conference on Learning Representations (ICLR).



