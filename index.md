---
title: Introduction
layout: home
nav_order: 1
---

# Improving Network Accuracy via Network Manipulation
{: .fs-9 }

---

## Introduction - Deep Learning
Deep Neural Networks consist of a large number of hidden layers and units, the functionality of which we are not fully aware. While we may understand feature engineering at the input level and the final output classification, the intermediate hidden features are somewhat of a "black box". It is not clear how the network is solving a task of high complexity. However, it has been observed that many hidden units are actually associated with concepts that are human-interpretable. Thus, it becomes important to really understand the functionality and contribution that each of these hidden units has to the final output of the network. In order to understand this, network dissection is used - a method to correlate semantic concepts identified within a complex convolutional neural network (CNN). It aims to identify, visualize and quantify the contributions of each individual unit within a deep CNN. 

Findings from network dissection show us that different groups of neurons correspond to different human-interpretable concepts such as trees, snow, etc.
Taking this one step further, the goal of this paper will be to find out if we can improve a network's prediction accuracy given this information regarding each neuron's roles. Until recently, most methods that aims to improve neural networks do not include specific knowledge about these networks, such as regularization and fine-tuning. A method that we will implement in this paper is FocusedDropout: a dropout method that retains neurons that contain target-related features while discarding other neurons. Additionally, we are also incorporating input gradient regularization, which involves minimizing the rate of change of loss with respect to the input features. This is said to improve the robustness as well as the interpretability of the network.

