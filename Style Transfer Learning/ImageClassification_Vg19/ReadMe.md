In the case of transfer learning, we use a pre-trained model, VGGNet in our case, and remove its last fully connected layer since our task is not to classify the image. Here, we use the pre-trained weights of the model to update the candidate image instead of updating the model weights. Since there are no prebuilt functions to train these type of networks in Keras, we will use lots of custom functions.