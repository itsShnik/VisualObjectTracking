# VisualObjectTracking
Compilation of some of the visual object tracking algorithms I worked on

## Mosse Filter:
Reference : 
> [Visual object tracking using adaptive correlation filters](https://ieeexplore.ieee.org/document/5539960/)

## KCF
Reference:
> [High-Speed Tracking with Kernelized Correlation Filters](http://www.robots.ox.ac.uk/~joao/publications/henriques_tpami2015.pdf)<br>
> J. F. Henriques, R. Caseiro, P. Martins, J. Batista<br>
> TPAMI 2015

## Siamese Networks

A Siamese neural network is an artificial neural network that uses the same weights while working in tandem on two different input vectors to compute comparable output vectors. Siamese networks have proved to be of great applicaiton in the field of visual object tracking. The ability of Siamese networks to output comparable featur vectors which basically indicate the similarity between the input images / patches is exploited by many recent researchers in computer vision.

### Siam - FC 
---
> [Fully-Convolutional Siamese Networks for Object Tracking](https://arxiv.org/abs/1606.09549)

#### Network Architecture

![Network Architecture](Images/siamfc.jpg?raw=true)

#### Explanation

Both the reference image (usually the first frame labeled with the bounding box, ___Z___) and the search image (___X___) are encoded into deep feature maps by the same - and therefore siamese - fully convolutional neural networks indicated by ___&phi;___ here. The feature map produced from the reference image (___&phi;___(_Z_)) is used like a correlation filter which is convolved (\*) with the deep feature map of the search image to give the required score map, which is then used to get the bounding box coordinates.

#### Some Special Highlights

##### Fully Convolutional Architecture

A fully convolutional architechture allows a mapping function i.e ___&phi;___ to be used for images with different sizes, this brings out the essence of _Siamese_ nature of the function.

##### Logistic Loss Function

The siamese network is pretrained on a dataset of videos with available groundtruth. Both positive and negative pairs of images are used to obtain better accuracy. Negative logarithmic loss is implemented with stochastic gradient descent (SGD) to arrive at optimal parameters.

##### No Online Training

Only offline training is used for the network to achieve weights that can be used for objects of any class. This also helps in achieving a high FPS and therefore real-time tracking.

##### Conclusion

This algo lets us depart from the traditional online learning methodology employed in tracking, and show an alternative approach that focuses on learning strong embeddings in an offline phase. The experiments using deep learning show that deep embeddings provide a naturally rich source of features which can be used for various purposes including this one.

##### Advantages over the traditional methods

- No online tracking. This specially helps when an object disappears or is occluded by any other object as when the object reappears the tracker tries to catch the object again by searching over a certain region.
- Greater accuracy in terms of Estimated Average Overlap (EAO) because of using the deep features.

##### Disadvantages / Problems

- The algorithm works well in classification part of the tracking problem but still traditional methods are used to create search images and locate the required objects.


### SiamRPN
----

> [High Performance Visual Tracking with Siamese Region Proposal Network](http://openaccess.thecvf.com/content_cvpr_2018/html/Li_High_Performance_Visual_CVPR_2018_paper.html)

#### Network Architecture

![Network Architecture](Images/siamrpn.png?raw=true)

#### Explanation

SiamRPM is an extended version of SiamFC, combining the deep feature maps extracted from the fully convolutional network with the [Region Proposal Network](https://arxiv.org/pdf/1506.01497.pdf).

#### The Region Proposal Network

![](Images/RPN.png?raw=true)

Region Proposal Network is used to propose regions containing objects (called anchors) in an image and their corresponding objectivity scores. To serve the purpose two branches - one for score classification and the other for the coordinates’ regression - are required.

#### Some Special Highlights 

- The given network is trained end to end offline, but the detection frame performs online inference as one shot detection. The forward pass on the detection branch is performed to obtain the classification and regression output, thus getting the top proposals. 

#### Conclusion

The Siamese-RPN is trained end-to-end offline with large scale image pairs. During online tracking, the proposed framework is formulated as a local one shot detection task.

#### Advantages 
- This algorithm addresses the problem of _search-image location_ and hence the _object location_ with the help of a Region Proposal Network.
- The problem of tracking hereby is speculated and formulated as one shot detection, which opens the doors for using the object detection algorithms in tracking prospects.


### DaSiamRPN
----

> [Distractor-aware Siamese Networks for Visual Object Tracking](https://arxiv.org/abs/1808.06048)

#### Explanation

Features used in most Siamese tracking approaches can only discriminate foreground from the non-semantic backgrounds. The semantic backgrounds are always considered as distractors, which hinders the robustness of Siamese trackers. DaSiamRPN focuses on learning distractor-aware Siamese networks for accurate and long-term tracking. To this end, features used in traditional Siamese trackers are analyzed at first. It is observed that the imbalanced distribution of training data makes the learned features less discriminative. During the off-line training phase, an effective sampling strategy is introduced to control this distribution and make the model focus on the semantic distractors. During inference, a novel distractor-aware module is designed to perform incremental learning, which can effectively transfer the general embedding to the current video domain. In addition, DaSiamRPN extends the proposed approach for long-term tracking by introducing a simple yet effective local-to-global search region strategy.

#### Some Special Highlights

- Distractor aware training : Diverese categories of positive pairs can promote the generalization abilty, and using Semantic negative pairs can improve the discriminative ability.

- Distractor aware incremental learning and long term tracking are used. 

### SiamRPN++
----

> [SiamRPN++: Evolution of Siamese Visual Tracking with Very Deep Networks](https://arxiv.org/abs/1812.11703)

#### Network Architecture

![Network Arrhcitectur](Images/SiamRPN++.png?raw=true)

#### Explanation

SiamRPN++ as its name suggests is a better version of SiamRPN which uses deep networks (ResNet) to obtain feature maps. Moreover, it proposes a new model architecture to perform layer-wise and depth-wise aggregations, which not only further improves the accuracy but also reduces the model size.

#### Some Special Highlights

- [Layer-wise aggregation](https://arxiv.org/abs/1707.06484)
- Depth-wise cross correlation 

### SiamMask
----

> [Fast Online Object Tracking and Segmentation: A Unifying Approach](https://arxiv.org/abs/1812.05050)

## Non Siamese Networks

### ATOM
----

> [ATOM: Accurate Tracking by Overlap Maximization](https://arxiv.org/abs/1811.07628)

## Reinforcement Learning Based Approaches
