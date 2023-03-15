---
layout: default
title: Method - Input Gradient Regularization
nav_order: 5
---

# Input Gradient Regularization

Input Gradient Regularization was initially introduced as "double back-propagation", and involved training neural networks by minimizing quadratic loss of the network 
as well as the rate of change of loss with respect to the input features. In this particular implementation, cross-entropy loss is used instead. The goal of this 
approach is to ensure that even if any input changes slightly, the KL divergence between predictions and labels will not change significantly. In turn, it serves as 
an interesting means to prevent adversarial attacks. In our paper, we aim to implement this method to check for general improvement in network accuracy, and combine 
it with network dissection to check for improved accuracy and interpretability. We formulate our overall loss function for this method as:

![Alt Text](/Methods/IGR_Loss.png)

The object function is presented more concisely as:

![Alt Text](/Methods/IGR_obj.png)
