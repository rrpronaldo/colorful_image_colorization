# Colorful Image Colorization

This is a experimentation/implementation of the paper from [Richard Zhang](https://richzhang.github.io/), [Phillip Isola](http://web.mit.edu/phillipi/), [Alexei A. Efros](http://www.eecs.berkeley.edu/~efros/). In [ECCV, 2016](http://arxiv.org/pdf/1603.08511.pdf),
available in the [GitHub Repository](https://github.com/richzhang/colorization). 

I use the Google Colaboratory to run and test the models available in the Zhang et. al implementation. My ideia is to divide the image in parts and run a type of Convolution Layer to try increase the quality of colorization, because of the input of the model is a 256x256 image, and when we rezise the image we lost information and this result in a small quality in the final colorized image.

