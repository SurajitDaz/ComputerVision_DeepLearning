# Abstract:
### Problem statement: 
A deep learning model which can explain the contents of an image in the form of speech through caption generation with an attention mechanism on Flickr8K dataset will be created. 

### Use Case: 
The product is made as an accessary for the blind people so that they can understand any image with the help of speech. The caption generated through a CNN-RNN model will be converted to speech using a text to speech library. 
 
This problem statement is an application of both deep learning and natural language processing. The features of an image will be extracted by a CNN-based encoder and this will be decoded by an RNN model.

<b>The project is an extended application of</b> Show, Attend and Tell: Neural Image Caption Generation with Visual Attention paper.
 
The dataset is taken from the Kaggle website and it consists of sentence-based image descriptions having a list of 8,000 images that are each paired with five different captions which provide clear descriptions of the salient entities and events of the image.
 
#Project Pipeline
The broader pipelines which followed here is mentioned below. The major steps those are to be performed can be briefly summarized in the following four steps:
*	Data Understanding: Here, we need to load the data and understand the representation.
•	Data Preprocessing: In this step, we will process both images and captions to the desired format.
•	Train-Test Split: Combine both images and captions to create the train and test dataset.
•	Model Building: This is the stage where we will create your image captioning model by building Encoder, Attention and Decoder model.
•	Model Evaluation: Evaluate the models using greedy search and BLEU score.


