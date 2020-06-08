
# Intermediate-Version

As we have seen in the Baseline version we have trained and tested the model on the same image hence the basline model won't generalize well to the images it has not seen before.

So for that we will use another version called Intermediate version which will be trained on different set of images and then tested on different set of images.


### The basic concept of the Intermediate-version is :-

* **The feature extractor**
Our neural network will link the black and white image with their colored version.
Imagine you had to color black and white images — but with restriction that you can only see nine pixels at a time. You could scan each image from the top left to bottom right and try to predict which color each pixel should be.

![Screenshot (137)](https://user-images.githubusercontent.com/44902363/84069136-ab051d00-a9e7-11ea-92f4-f4012ac2d420.png)

 it’d be next to impossible to make a good colorization, so you break it down into steps.

First, you look for simple patterns: a diagonal line, all black pixels, and so on. You look for the same exact pattern in each square and remove the pixels that don’t match. You generate 64 new images from your 64 mini filters.

![Screenshot (138)](https://user-images.githubusercontent.com/44902363/84069358-06370f80-a9e8-11ea-9126-9042bcaf7359.png)

To get more underlying pattern you need to decrease the image size into half.
You now also have the 3x3 filter but when we combine this with lower level filter you will able to detect the complex pattern.

* **From feature extraction to color** 

The neural network operates in a trial and error manner. It first makes a random prediction for each pixel. Based on the error for each pixel, it works backward through the network to improve the feature extraction.

It starts adjusting for the situations that generate the largest errors. In this case, the adjustments are: whether to color or not, and how to locate different objects.

The network starts by coloring all the objects brown. It’s the color that is most similar to all other colors, thus producing the smallest error.

### Technical Explanation:-

The main difference from other visual neural networks is the importance of pixel location. In coloring networks, the image size or ratio stays the same throughout the network. In other types of network, the image gets distorted the closer it gets to the final layer.

The max-pooling layers in classification networks increase the information density, but also distort the image. It only values the information, but not the layout of an image. In coloring networks we instead use a stride of 2, to decrease the width and height by half. This also increases information density but does not distort the image.

Two further differences are: upsampling layers and maintaining the image ratio. Classification networks only care about the final classification. Therefore, they keep decreasing the image size and quality as it moves through the network.

Coloring networks keep the image ratio constant. This is done by adding white padding. Otherwise, each convolutional layer cuts the images. It’s done with the *padding='same'*parameter.

To double the size of the image, the coloring network uses an upsampling layer.

![Screenshot (139)](https://user-images.githubusercontent.com/44902363/84071512-74310600-a9eb-11ea-8f84-163fb5f7a4a9.png)


This for-loop first counts all the file names in the directory. Then, it iterates through the image directory and converts the images into an array of pixels. Finally, it combines them into a giant vector.

![Screenshot (140)](https://user-images.githubusercontent.com/44902363/84072054-341e5300-a9ec-11ea-920a-41766fed5c73.png)


With ImageDataGenerator, we adjust the setting for our image generator. This way, each image will never be the same, thus improving the learning rate. The shear_rangetilts the image to the left or right, and the other settings are zoom, rotation and horizontal-flip.

![Screenshot (141)](https://user-images.githubusercontent.com/44902363/84072280-8fe8dc00-a9ec-11ea-9b63-e84535902ad8.png)

We use the images from our folder, Xtrain, to generate images based on the settings above. Then, we extract the black and white layer for the X_batch and the two colors for the two color layers.
