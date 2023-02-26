---
title: Introduction
layout: home
nav_order: 1
---

# Improve Accuracy via Network Dissection
{: .fs-9 }

---

## Introduction - Deep Learning
Deep Neural Networks consist of a large number of hidden layers and units, the functionality of which we are not fully aware. While we may understand feature engineering at the input level and the final output classification, the intermediate hidden features are somewhat of a "black box". It is not clear how the network is solving a task of high complexity. However, it has been observed that many hidden units are actually associated with concepts that are human-interpretable. Thus, it becomes important to really understand the functionality and contribution that each of these hidden units has to the final output of the network. In order to understand this, network dissection is used - a method to correlate semantic concepts identified within a complex convolutional neural network (CNN). It aims to identify, visualize and quantify the contributions of each individual unit within a deep CNN. 

Findings from network dissection show us that different groups of neurons correspond to different human-interpretable concepts such as trees, snow, etc.
Taking this one step further, the goal of this paper will be to find out if we can improve a network's prediction accuracy given this information regarding each neuron's roles. Until recently, most methods that aims to improve neural networks do not include specific knowledge about these networks, such as regularization and fine-tuning. A method that we will implement in this paper is FocusedDropout: a dropout method that retains neurons that contain target-related features while discarding other neurons. Additionally, we are also incorporating input gradient regularization, which involves minimizing the rate of change of loss with respect to the input features. This is said to improve the robustness as well as the interpretability of the network.

---

## Network Dissection
The process of network dissection can determine what visual concept in the real world a unit most strongly represents despite not explicitly teaching the model this concept in the training data. The validity of network dissection can be tested by activating or deactivating units based on our new understanding of the encoded representation to determine the importance of the unit to the model performance in specific tasks. By understanding the role of hidden units, we would have a better understanding of network structure, enable interaction between humans and models, and understand how adversarial attacks work.

There are a few previous approaches to solve the problem: salience map, simplified surrogate model, and training explanation network. The salience map approach presents the position of an input image that the network would look at making a decision. Although this helps clarify how a neural network decides on a prediction through a simulation of human sight, this approach lacks an explanation of the weights within the model. An explanation like this tends to be more general rather than our desired approach of understanding individual units and how they work together. The simplified surrogate model is used to simplify the complex behavior of neural networks and training explanation networks generate explanations that can be interpreted by humans. However, these two approaches have huge flaws as they not only fail to directly explain the internal computation of a neural network, but also require training an entire auxiliary model. The commitment of time and resources for these approaches may not be practical for the understanding we wish to achieve. We present a network dissection algorithm which explores the neural network more in depth. Network dissection provides direct examination of the unit weights and is effective without the need to train an auxiliary model. This would allow for greater focus in analysis as a human interface for controlling the network and even gain insight about the black box internals of neural networks.

A strength of network dissection is that the key idea relates to analyzing the visual concept associated with units within the network, which is a concept that image-based neural networks employ. Thus, network dissection can be applied to a wide range of models rather than specific model architectures that the algorithm is particularly designed for. While this does restrict network dissection to image-based tasks, the versatility of network dissection streamlines the understanding of this type of model significantly. In addition, network dissection can be applied to multiple different tasks, as long as the units learn relations to visual concepts. This is exemplified within this paper as network dissection is applied to image classification. The variety of tasks and model architectures that network dissection applies to without the need of heavy customization makes it a powerful tool to analyze the role of individual hidden units and find insights about the black box natures of neural networks.

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"></a>
  </li>
{% endfor %}
</ul>
---

## Methods
### FocusedDropout
FocusedDropout is a highly targeted approach that makes the network focus on the most important features (based on the idea of Network Dissection) while dropping other features. The methodology for FocusedDropout is shown as Figure 1. To get a visual understanding of FocusedDropout, Figure 2 shows the process of creating the binary mask that will be applied to every channel based on the highest activation channel. For this paper, we will be using ResNet-18 for the CNN and CIFAR-10 for the dataset.
### Input Gradient Regularization
Input Gradient Regularization was initially introduced as "double back-propagation", and involved training neural networks by minimizing quadratic loss of the network as well as the rate of change of loss with respect to the input features. In this particular implementation, cross-entropy loss is used instead. The goal of this approach is to ensure that even if any input changes slightly, the KL divergence between predictions and labels will not change significantly. In turn, it serves as an interesting means to prevent adversarial attacks. In our paper, we aim to implement this method to check for general improvement in network accuracy, and combine it with network dissection to check for improved accuracy and interpretability. We formulate our overall loss function for this method as:

The object function is presented more concisely as:

---

## Result

---

## Conclusion



This is a *bare-minimum* template to create a Jekyll site that uses the [Just the Docs] theme. You can easily set the created site to be published on [GitHub Pages] – the [README] file explains how to do that, along with other details.

If [Jekyll] is installed on your computer, you can also build and preview the created site *locally*. This lets you test changes before committing them, and avoids waiting for GitHub Pages.[^1] And you will be able to deploy your local build to a different platform than GitHub Pages.

More specifically, the created site:

- uses a gem-based approach, i.e. uses a `Gemfile` and loads the `just-the-docs` gem
- uses the [GitHub Pages / Actions workflow] to build and publish the site on GitHub Pages

Other than that, you're free to customize sites that you create with this template, however you like. You can easily change the versions of `just-the-docs` and Jekyll it uses, as well as adding further plugins.

[Browse our documentation][Just the Docs] to learn more about how to use this theme.

To get started with creating a site, just click "[use this template]"!

----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
