# ResNet50-with-CIFAR10-from-scratch

This notebook has implementation of ResNet50 from scratch and is trained for multi-class classification over CIFAR-10 dataset 

The details of the implementation can be found in the ResNet Paper ["Deep Residual Learning for Image Recognition"](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper.pdf) and the details of the dataset can be found here: [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html)

ResNet was proposed by Microsoft in 2015 in the ILSVRC. Multiple ResNet architecture were proposed, now even there are ResNets consisting of over a thousand layers. That time ResNet set new records in classification, detection, and localization through one single incredible architecture. Besides the new record in terms of number of layers, ResNet won ILSVRC 2015 with an incredible error rate of 3.6% ( humans generally hover around a 5-10% error rate).

#### Residual Block
The idea behind a residual block is that you have your input x go through conv-relu-conv series. This will give you some F(x). That result is then added to the original input x. Let’s call that H(x) = F(x) + x. In traditional CNNs, your H(x) would just be equal to F(x) right? So, instead of just computing that transformation (straight from x to F(x)), we’re computing the term that you have to add, F(x), to your input, x. Basically, the mini module shown below is computing a “delta” or a slight change to the original input x to get a slightly altered representation (When we think of traditional CNNs, we go from x to F(x) which is a completely new representation that doesn’t keep any information about the original x). The authors believe that “it is easier to optimize the residual mapping than to optimize the original, unreferenced mapping”.

<p align="center"><img src="./images/resnet50_3.png" width="400"> </p>


Another reason for why this residual block might be effective is that during the backward pass of backpropagation, the gradient will flow easily through the graph because we have addition operations, which distributes the gradient.

<img align="left" img src="./images/resnet50_2.png" width="400" height="700"> <img align="right" img src="./images/resnet50_1.png" width="500"  height="600">
