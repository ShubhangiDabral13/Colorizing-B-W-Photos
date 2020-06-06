
## Basline-Version :-

In baseline version we just worked on one image so that syntax and the core concept will be clear and then as we walk through this project we are going to add more features to our baseline.

We just a basic model we made the following transformation.

* This is the orginal picture:-

![dog](https://user-images.githubusercontent.com/44902363/83952259-3f8b4600-a855-11ea-9e75-3cea385edccb.jpg)

* This picture is done by our neural network

![img_result](https://user-images.githubusercontent.com/44902363/83952272-5467d980-a855-11ea-88dd-fbde5b83d75d.png)



In baseline version the neural-network is trained and tested on same image.

#### What is done in Baseline version
* hanging RGB color to Lab.
L stands for lightness, and a and b for the color spectra green–red and blue–yellow.

eg:-

![Lab](https://user-images.githubusercontent.com/44902363/83952499-de647200-a856-11ea-881f-959facbe6572.jpg)

a Lab encoded image has one layer for grayscale, and has packed three color layers into two. This means that we can use the original grayscale image in our final prediction. Also, we only have two channels to predict.

* From B&W to color
Our final prediction looks like this. We have a grayscale layer for input, and we want to predict two color layers, the ab in Lab. To create the final color image we’ll include the L/grayscale image we used for the input. The result will be creating a Lab image.

![lab2](https://user-images.githubusercontent.com/44902363/83952705-1a4c0700-a858-11ea-8407-9ff4e7c5ed15.png)

 The black and white layer is our input and the two colored layers are the output.
 
 ![Screenshot (129)](https://user-images.githubusercontent.com/44902363/83952771-e7eed980-a858-11ea-88b6-73af1e9f98d8.png)

We map the predicted values and the real values within the same interval. This way, we can compare the values. The interval ranges from -1 to 1. To map the predicted values, we use a tanh activation function. For any value you give the tanh function, it will return -1 to 1.

The true color values range between -128 and 128. This is the default interval in the Lab color space. By dividing them by 128, they too fall within the -1 to 1 interval. This “normalization” enables us to compare the error from our prediction.

After calculating the final error, the network updates the filters to reduce the total error. The network continues in this loop until the error is as low as possible.

![Screenshot (130)](https://user-images.githubusercontent.com/44902363/83952868-b32f5200-a859-11ea-80ef-7d8a6101d944.png)

1.0/255 indicates that we are using a 24-bit RGB color space. It means that we are using numbers between 0–255 for each color channel.

![Screenshot (132)](https://user-images.githubusercontent.com/44902363/83952929-233dd800-a85a-11ea-8606-6a05e85439fc.png)

We match it with our neural network, which also returns values between -1 and 1.

After converting the color space using the function rgb2lab() we select the grayscale layer with: [ : , : , 0]. This is our input for the neural network. [ : , : , 1: ] selects the two color layers, green–red and blue–yellow.

After training the neural network, we make a final prediction which we convert into a picture.

![Screenshot (133)](https://user-images.githubusercontent.com/44902363/83953493-79ad1580-a85e-11ea-9971-99fa123b611d.png)

Here, we use a grayscale image as input and run it through our trained neural network. We take all the output values between -1 and 1 and multiply it by 128. This gives us the correct color in the Lab color spectrum.

![Screenshot (133)](https://user-images.githubusercontent.com/44902363/83953602-27202900-a85f-11ea-9099-822a0e7d66ee.png)


Lastly, we create a black RGB canvas by filling it with three layers of 0s. Then we copy the grayscale layer from our test image. Then we add our two color layers to the RGB canvas. This array of pixel values is then converted into a picture.


