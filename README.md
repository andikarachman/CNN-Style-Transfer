# CNN-Style-Transfer

In this notebook, we’ll create a style-transfer method by utilizing convolutional neural networks. In style-transfer method, we attempt to modify the style of an image while preserving its content. The general idea is to take two images, and produce a new image that reflects the content of one but the artistic style of the other. The implementation of the style-transfer method will be performed in PyTorch.  

In this notebook, we will implement the style transfer technique from the article [Image Style Transfer Using Convolutional Neural Networks, by Gatys](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf). In this article, style transfer uses the features found in the 19-layer VGG Network (VGG19), which is comprised of a series of convolutional and pooling layers, and a few fully-connected layers. In the image below, the convolutional layers are named by stack and their order in the stack. The structure of VGG19 is shown below:

<img src='assets/VGG19.jpg'/>


### Creating a style-transfer method

1. First, we take content image and style images and resize them to equal shapes. 
2. Then, we load a pre-trained VGG19.
3. Knowing that we can distinguish layers that are responsible for the style (basic shapes, colors etc.) and the ones responsible for the content (image-specific features), we can separate the layers to independently work on the content and style.
4. Then we set our task as an optimization problem where we are going to minimize:
   - **content loss**, i.e., the distance between the input and output images. We minimize this loss to preserve the content of the image. 
   - **style loss**, i.e., the distance between the style and output images. We minimize this loss to apply a new style to an image.
   - **total variation loss**, i.e., regularization - spatial smoothness to denoise the output image.
5. Finally, we set our gradients and optimize with the Adam optimizer.

This project is inspired by one of the mini-projects in the Udacity Deep Learning Nanodegree.
