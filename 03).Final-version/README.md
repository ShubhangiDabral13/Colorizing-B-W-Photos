
# Final-Version

To make our version more advance and also for better result we will futher modify our Intermediate-version.

## Detail overview about Final-version:

Our final version of the colorization neural network has four components. We split the network we had before into an encoder and a decoder. Between them, we’ll use a fusion layer.

In parallel to the encoder, the input images also run through one of today’s most powerful classifiers — the Inception ResNet v2 . This is a neural network trained on 1.2M images. We extract the classification layer and merge it with the output from the encoder.

![Screenshot (198)](https://user-images.githubusercontent.com/44902363/85519466-2b9a5f00-b61f-11ea-82d6-0644038374dc.png)


By transferring the learning from the classifier to the coloring network, the network can get a sense of what’s in the picture. Thus, enabling the network to match an object representation with a coloring scheme.

## Technical Explanation:

* First, we download the Inception ResNet v2 neural network and load the weights. Since we will be using two models in parallel, we need to specify which model we are using. This is done in Tensorflow, the backend for Keras.

![Screenshot (201)](https://user-images.githubusercontent.com/44902363/85519897-d3179180-b61f-11ea-9a18-55e003453812.png)


* To create our batch, we use the tweaked images. We convert them to black and white and run them through the Inception ResNet model.

![Screenshot (202)](https://user-images.githubusercontent.com/44902363/85520216-3acddc80-b620-11ea-953a-e0d3776103e0.png)


* First, we have to resize the image to fit into the Inception model. Then we use the preprocessor to format the pixel and color values according to the model. In the final step, we run it through the Inception network and extract the final layer of the model.

![Screenshot (203)](https://user-images.githubusercontent.com/44902363/85520405-7ff20e80-b620-11ea-8056-69a7edc145fa.png)


* Let’s go back to the generator. For each batch, we generate 20 images in the below format. It takes about an hour on a Tesla K80 GPU. It can do up to 50 images at a time with this model without having memory problems.

![Screenshot (204)](https://user-images.githubusercontent.com/44902363/85521291-a82e3d00-b621-11ea-9c69-2531b70558b9.png)


* encoder_input is fed into our Encoder model, the output of the Encoder model is then fused with the embed_input in the fusion layer; the output of the fusion is then used as input in our Decoder model, which then returns the final output, decoder_output.





