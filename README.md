# Colorful Image Colorization

## Zhang et al. Project

This is a experimentation/implementation of the paper from [Richard Zhang](https://richzhang.github.io/), [Phillip Isola](http://web.mit.edu/phillipi/), [Alexei A. Efros](http://www.eecs.berkeley.edu/~efros/). In [ECCV, 2016](http://arxiv.org/pdf/1603.08511.pdf),
available in the [GitHub Repository](https://github.com/richzhang/colorization). 

Convolutional Neural Networks was the technique that Zhang et al. used to image colorization. The propose is to forecast what an input grayscale image would looks like when colorized. The architecture of neural network is showed in the image bellow:

![image](https://user-images.githubusercontent.com/48371088/121775539-b640da80-cb5e-11eb-85b9-7e021833de28.png)

The input of the Neural Network is a layer of the image with the size 256 x 256 pixels. This layer is the "L" channel from [CIELAB color space](https://en.wikipedia.org/wiki/CIELAB_color_space), or just LAB. It's similar to the RBG color space and has tree channels. But unlike the RGB, Lab encodes color information differently:
 * The L channel encodes lightness intensity only;
 * The a channel encodes green-red;
 * And the b channel encodes blue-yellow.

Since the L channel encodes only the intensity, this can be used as grayscale input to the network. From there the network must learn to predict the a and b channels. Given the input L channel and the predicted ab channels we can then form our final output color image.

The image colorization process can be summarized as:
 * Resize the image into 256x256 dimensions (these are the dimensions of Neural Network input);
 * Convert the image from the RGB color space to the Lab color space;
 * Use the L channel as the input to the network and train the network to predict the a and b channels;
 * Combine the input L channel with the predicted ab channels and resize to the original image size;
 * Finally, convert the LAB image back to RGB.

To train the network, Zhang et al. used the ImageNet dataset and converted all images from the RGB color space to the Lab color space and followed the steps above.

___

There's also an excellent guide on the Adrian [pyimagesearch site](https://www.pyimagesearch.com/2019/02/25/black-and-white-image-colorization-with-opencv-and-deep-learning/). This guide uses an implemation with caffe model, wich I use in others tests.

___

## My project
I use the Google Colaboratory to run and test the models available in the Zhang et. al implementation. My ideia is to divide the image in parts and run a type of Convolution and Pooling Layer to try increase the quality of colorization. The reason for this is because of the input of the model is a 256x256 image, and when we rezise the image we lost information and this result in a small quality in the final colorized image.

I'm going to take chunks of the L channel from original image size and go through the Colorization Model. Then I'll combine each result piece of the ab channel into a final matrix that was the same size as the original image. I test this theory with different kernel types (scrolling across the image) and chunks sizes. I combine the results in the matrix with the average or maximum pooling technique.

The quality of the result color images depends on the environment of each photo. For example if a photo is outdoors or indoors. So far, the best results have been in natural environments.

A next research could be to build a pre-trained model with Tensorflow, then add a final layer that trains with the specific type of images that we expect to use. For example, training last layer with images of plants, soldiers, animals, just outdoors, just indoors, and so on. This could produce good results, but until now it's just a thesis.

The process of Convolution Neural Network is express bellow:

![image](https://user-images.githubusercontent.com/48371088/121779974-9b796080-cb74-11eb-8fcd-d52544550179.png)


