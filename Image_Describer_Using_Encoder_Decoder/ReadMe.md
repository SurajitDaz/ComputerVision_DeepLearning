# Abstract:
### Problem statement: 
A deep learning model which can explain the contents of an image in the form of speech through caption generation with an attention mechanism on Flickr8K dataset will be created. 

### Use Case: 
The product is made as an accessary for the blind people so that they can understand any image with the help of speech. The caption generated through a CNN-RNN model will be converted to speech using a text to speech library. 
 
# DataSet:  
The dataset is taken from the [Kaggle website](https://www.kaggle.com/datasets/adityajn105/flickr8k) and it consists of sentence-based image descriptions having a list of 8,000 images that that is publicly available and contains 8,000 images depicting various scenarios and events. Each data point is properly labelled with five captions. One of the major benefits of working with this data set is that its size is small, which makes it easier for users to work on it on low-end PCs
 
# Technical Aspects:
This problem statement is an application of both deep learning and natural language processing. The features of an image will be extracted by a CNN-based encoder and this will be decoded by an RNN model. <b>The project is an extended application of</b> Show, Attend and Tell: Neural Image Caption Generation with Visual Attention paper.

The broader pipelines which followed here is mentioned below. The major steps those are to be performed can be briefly summarized in the following four steps:
*	Data Understanding: Here, we need to load the data and understand the representation.
*	Data Preprocessing: In this step, we will process both images and captions to the desired format.
*	Train-Test Split: Combine both images and captions to create the train and test dataset.
*	Model Building: This is the stage where we will create your image captioning model by building Encoder, Attention and Decoder model.
*	Model Evaluation: Evaluate the models using greedy search and BLEU score.


