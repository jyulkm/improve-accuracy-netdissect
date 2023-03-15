---
layout: default
title: Discussion
nav_order: 5
---

# Discussion

Based on the images from Network Dissection, we see that VGG16 on CIFAR100 does not detect scenes that well while the reported result (VGG16 on Places365) shows clear classifications of high-level concepts. This is highly suspected due to the fact that CIFAR100 is a dataset that revolves around object detection while Places365 is a dataset that revolves around scene detection. This difference in the datasets might prevent our model from learning high-level concepts. Additionally, CIFAR100 is a subset of a much bigger dataset and we feel that using a larger dataset will also allow for better generalization and conceptual understanding.

A next step for this project would be to train our VGG16 models on Places365. This was not done in this project due to limited resources: it was estimated to take around 50 days for our model to train on Places365 for 100 epochs with our GPU. As a result, we stuck with CIFAR100 for this project.

Through this project, we see that a network’s information can be utilized to manipulate the network to achieve better performance.
