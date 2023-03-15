---
title: Method - Network Dissection Intervention
layout: home
nav_order: 3
---

# Network Dissection Intervention
{: .fs-9 }

Network dissection intervention is the process of modifying internal representations to improve the performance of the network on a specific task. 
For example, if a network is trained to recognize images of cars, but it is found that it has trouble distinguishing between different models of cars, 
network dissection intervention can be used to identify the units that are responsible for recognizing different car models and modify them to improve 
performance on this task. As we use Places365 data,  we calculate the accuracy for every 365 classes by removing one unit at once and determine which unit 
assists the network by increasing accuracy. After dividing units into good and bad, we reduce the weights or output of bad units.
