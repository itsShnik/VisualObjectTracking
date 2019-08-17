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

> [Fully-Convolutional Siamese Networks for Object Tracking](https://arxiv.org/abs/1606.09549)

#### Network Architecture

![Network Architecture](Images/siamfc.jpg?raw=true)

#### Explanation

Both the reference image (usually the first frame labeled with the bounding box, ___Z___) and the search image (___X___) are encoded into deep feature maps by the same - and therefore siamese - fully convolutional neural networks indicated by _&phi;_ here. The feature map produced from the reference image (___&phi;___(_Z_)) is used like a correlation filter which is convolved (\*) with the deep feature map of the search image to give the required score map, which is then used to get the bounding box coordinates.


### SiamRPN

> [High Performance Visual Tracking with Siamese Region Proposal Network](http://openaccess.thecvf.com/content_cvpr_2018/html/Li_High_Performance_Visual_CVPR_2018_paper.html)

### DaSiamRPN

> [Distractor-aware Siamese Networks for Visual Object Tracking](https://arxiv.org/abs/1808.06048)

### SiamRPN++

> [SiamRPN++: Evolution of Siamese Visual Tracking with Very Deep Networks](https://arxiv.org/abs/1812.11703)

### SiamMask

> [Fast Online Object Tracking and Segmentation: A Unifying Approach](https://arxiv.org/abs/1812.05050)

### ATOM

> [ATOM: Accurate Tracking by Overlap Maximization](https://arxiv.org/abs/1811.07628)

