# Abstract:
### Problem statement: 
A deep learning model which can explain the contents of an image in the form of speech through caption generation with an attention mechanism on Flickr8K dataset will be created. 

### Use Case: 
The product is made as an accessary for the blind people so that they can understand any image with the help of speech. The caption generated through a CNN-RNN model will be converted to speech using a text to speech library.<br><br><br>
 

# DataSet:  
The dataset is taken from the [Kaggle website](https://www.kaggle.com/datasets/adityajn105/flickr8k) and it consists of sentence-based image descriptions having a list of 8,000 images that that is publicly available and contains 8,000 images depicting various scenarios and events. Each data point is properly labelled with five captions. One of the major benefits of working with this data set is that its size is small, which makes it easier for users to work on it on low-end PCs. <br><br><br>
 

# Methodology:
### Project Pipe:
This problem statement is an application of both deep learning and natural language processing. The features of an image will be extracted by a CNN-based encoder and this will be decoded by an RNN model. <b>The project is an extended application of</b> Show, Attend and Tell: Neural Image Caption Generation with Visual Attention paper.

The broader pipelines which followed here is mentioned below. The major steps those are to be performed can be briefly summarized in the following four steps:
*	Data Understanding: Here, we need to load the data and understand the representation.
*	Data Preprocessing: In this step, we will process both images and captions to the desired format.
*	Train-Test Split: Combine both images and captions to create the train and test dataset.
*	Model Building: This is the stage where we will create your image captioning model by building Encoder, Attention and Decoder model.
*	Model Evaluation: Evaluate the models using greedy search and BLEU score.

### CNN-RNN model:
The image-to-caption generation part can be achieved with the help of encoder-decoder (CNN-RNN) based models. The encoder parts involve the convolution of the input image with the help of various convolution, max pooling, and fully connected layers. Since we are not dealing with the classification of the image, we have removed them from the end. The final output of the encoder part will be the generation of the feature vector.
After the generation of the feature vector, we will focus on the decoder portion. The decoder portion is an RNN based model. The basic difference between CNN and RNN is feedback memory. A particular RNN layer is a function of the present input along with the previous input. So, in our project, the RNN layers will have two inputs, one is the feature vector and the other is the output of the previous layer.
 
Aa first, the image will be passed through the encoder, and the feature vector will be generated. Then, the first RNN layer will have this feature vector and the <start> tag as the input and will generate the first word of the sequence. The next layer will have this predicted word and the feature vector as the input and will predict the second word. This series of events will continue until you find the <end> tag as the output. Words are predicted by finding the probabilities of the occurrence of the word in the dictionary.
 
 Now, in traditional CNN-RNN based model is not the perfect model to extract the contents of an image. The model has a limitation because of which unnecessary information is passed through the model and the predictions can vary because of this limitation. So, one of the major limitations of the traditional methods is with the input of the image which ultimately is passed as the input to every RNN layer at every timestamp that can pass unnecessary information into the model and can, in turn, decrease the computational speed of the entire model. Owing to this limitation, the model suffers in predicting the word sequence correctly.

So, to overcome this problem, instead of passing the complete image at each timestamp, we can only pass the necessary parts of the image that can help in the prediction of the image at every timestamp. Thus, the model will run faster and increase its prediction accuracy.

This limitation can be solved with the help of an attention mechanism.
 
 ### Attention model:
 Now, we will pass two inputs to the RNNs – one is the output of the previous layer and the second is the output coming from the attention model, i.e. the context vector. The context vector is highlighted differently at each timestamp. For the next RNN, the previous input will be passed along with a different highlighted area of the image.
 
In a primitive model, we assume that the spatial dimensions of the CNN image features were averaged together. Now, we describe a method to weight these spatial locations according to their perceived importance. This technique is referred to as an attention mechanism.

For a particular word, more than one area in the context vector can help in prediction. Hence, we take the weighted sum of all the areas and pass it to the decoder. The below image demonstrates the line “Attention Is All You Need”. 
![attention](https://user-images.githubusercontent.com/75905023/224535164-d7b39b1b-a2a4-44f2-a52e-49dfd12da32e.gif)
 
 A “classic” image captioning system would encode the image, using a pre-trained Convolutional Neural Network that would produce a feature vector. This feature vector would remain the same while decoding the caption using RNN. However, with an attention model, we get a varying feature vector based on the previously generated word. This helps you to look at different parts of the image for better captioning.
 
When the RNN is generating a new word, the attention mechanism is focusing on the relevant part of the image, so the decoder only uses specific parts of the image.
 
To an attention model, which is a kind of neural network, we pass in $$h_t$$ (decoder's hidden state) and $$f_j$$ (feature vector coming from the encoder).  Therefore with this information, you can get how important is the jthpixel of the input image at the tth time stamp.
 
This is represented by the equation: $$e_{jt}=f_{att}(ht,fj)$$



