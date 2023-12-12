---
layout: distill
title: Training Robust Networks
description: "Exploring ResNet on TinyImageNet, unveiling brittleness and discovering robustment enhancement strategies via hyperparameter optimization"
date: 2023-12-12
htmlwidgets: true

# Anonymize when submitting
# authors:
#   - name: Anonymous

authors:
  - name: Jackie Lin
    affiliations:
      name: MIT
  - name: Nten Nyiam
    affiliations:
      name: MIT

# Must be the exact same name as your blogpost
bibliography: 2023-12-12-training-robust-networks.bib

# Add a table of contents to your post.
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
toc:
  - name: Introduction
  - name: Related Works
  - name: Methodology
  - name: Results
  - name: Conclusion and Next Steps

# Below is an example of injecting additional post-specific styles.
# This is used in the 'Layouts' section of this post.
# If you use this post as a template, delete this _styles block.
---
# Introduction
In the recent years, deep neural networks have emerged as a dominant force in the field of machine learning, achieving remarkable success across a variety of tasks, from VGG-16 in image classification to ChatGPT in natural language modeling. However, the very complexity that allows deep neural networks to learn and represent complex patterns and relationships can also leave them susceptible to challenges such as overfitting, adversarial attacks, and interpretability. The brittleness of deep neural networks, in particular, poses a significant challenge toward their deployment in real-world applications, especially those where reliability is paramount, like medical image diagnosis and autonomous vehicle navigation. Consequently, it is crucial to develop a better understanding of deep architectures and explore strategies for enhancing robustness. This project focuses specifically on ResNet, a model introduced in 2015 for image classification that is still widely used today. In particular, we will study the model's vulnerability to adversarial perturbations and, subsequently, work through a strategy to enhance its resilience through data augmentation and hyperparameter optimization. 

# Related Works 
ResNet<d-cite key="resnet2015"></d-cite> is a convolutional neural network architecture introduced in 2015 that sought to overcome numerical instability issues in deep networks and simplify the complexity of architecture search. It achieved this by incorporating skip connections, essentially allowing the training procedure to dynamically determine the optimal number of layers for the network. ResNet is trained on ImageNet<d-cite key="imagenet2014"></d-cite>, a popular benchmark in object category classification with a thousand classes and millions of images. For our project, we will use ResNet-18, a version of the original ResNet-34 model that is 18 layers deep, and TinyImageNet, a smaller version of ImageNet with around a hundred thousand images (64x64) and 200 classes. This is largely for computational ease. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2023-12-12-training-robust-networks/resnet.png" class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Figure 1. ResNet-18 Architecture
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2023-12-12-training-robust-networks/tinyimagenet.png" class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Figure 2. Sample Images from TinyImageNet
</div>

The brittleness of many deep neural networks for computer vision is well documented. For example, adding a tiny amount of random Gaussian noise, imperceptible to the human eye, can dramatically affect the accuracy and confidence of a network. In fact, we can optimize the input image to maximize the prediction error, generating small, non-random perturbations that we can use to alter the network's prediction behavior arbitrarily, a vulnerability that applies to a variety of networks<d-cite key="brittleness1"></d-cite><d-cite key="brittleness2"></d-cite>. 

In this project, we investigate two small perturbations: adding random Gaussian noise and modifying the colors of a small subset of pixels. We use hyperparameter search to finetune ResNet-18, aiming to create network robust to these pertubations without compromising significantly on accuracy. Specifically, we examine general hyperparameters like batch size, learning rate, number of frozen layers, and more. The ultimate goal is to define a straightforward and resource-efficient strategy for mitigating brittleness that can potentially be extended to other architectures and domains. 

# Methodology


# Results 

# Conclusion and Next Steps