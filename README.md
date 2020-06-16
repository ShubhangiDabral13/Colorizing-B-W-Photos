# Colorizing-Black-And-white-Images

### About:-
In this project uses Convolution Neural Network(generative adversarial networks) to add color to black and white images. For each such image, the generator network (G) receives its black and white version and outputs a full RGB version of the image (i.e. the black and white image with color added to it).

## Core-Logic:-

Black and white images can be represented in grids of pixels. Each pixel has a value that corresponds to its brightness. The values span from 0–255, from black to white.

![Screenshot (153)](https://user-images.githubusercontent.com/44902363/84785519-347ca680-b009-11ea-92c5-f24d4b98d6ba.png)

Color images consist of three layers: a red layer, a green layer, and a blue layer. This might be counter-intuitive to you. Imagine splitting a green leaf on a white background into the three channels. Intuitively, you might think that the plant is only present in the green layer.

But, as you see below, the leaf is present in all three channels. The layers not only determine color, but also brightness.

![Screenshot (156)](https://user-images.githubusercontent.com/44902363/84785659-5d9d3700-b009-11ea-9962-b491be467dd8.png)


To achieve the color white, for example, you need an equal distribution of all colors. By adding an equal amount of red and blue, it makes the green brighter. Thus, a color image encodes the color and the contrast using three layers:

![Screenshot (154)](https://user-images.githubusercontent.com/44902363/84785790-86253100-b009-11ea-910c-ab0e6810c3a9.png)


Just like black and white images, each layer in a color image has a value from 0–255. The value 0 means that it has no color in this layer. If the value is 0 for all color channels, then the image pixel is black.

As you may know, a neural network creates a relationship between an input value and output value. To be more precise with our colorization task, the network needs to find the traits that link grayscale images with colored ones.

In sum, we are searching for the features that link a grid of grayscale values to the three color grids.

![Screenshot (155)](https://user-images.githubusercontent.com/44902363/84786111-f03dd600-b009-11ea-9d18-76b41cac2fe4.png)

Hence to implement this we will make colorization neural net in three steps.

* The first section breaks down the core logic. We’ll build a bare-bones 40-line neural network as an “Baseline” colorization bot. There’s not a lot of magic in this code snippet. This well help us become familiar with the syntax.

* The next step is to create a neural network that can generalize — our “Intermeditate” version. We’ll be able to color images the bot has not seen before.

* For our “final” version, we’ll combine our neural network with a classifier. We’ll use an Inception Resnet V2 that has been trained on 1.2 million images. To make the coloring pop, we’ll train our neural network on portraits from Unsplash.

### Inspiration from
  * https://github.com/emilwallner/Coloring-greyscale-images


### Author:-

#### Shubhangi Dabral (ShubhangiDabral13)
<a href="https://twitter.com/Shubhi_Dabral"><img 
src="https://news.wjct.org/sites/wjct/files/styles/medium/public/201407/v65oai7fxn47qv9nectx.png" align="left" height="50" width="50" ></a>
<a href="https://www.linkedin.com/in/shubhangi-dabral-b79705145/"><img src="https://cdn2.iconfinder.com/data/icons/simple-social-media-shadow/512/14-512.png" align="left" height="60" width="60" ></a>


