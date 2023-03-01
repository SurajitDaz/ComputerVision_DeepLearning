
#Summary
In this session, you learnt to set-up a typical end-to-end pipeline for training CNNs. Specifically, you learnt the following:

 

##Data preprocessing
###Morphological Transformations: This refers to changing the shape and size of images. The typical transformations are erosion, dilation, opening and closing. 

 

###Augmentation: Refers to making changes related to rotation, translation, shearing, etc. Augmentation is often used in image-based deep learning tasks to increase the amount and variance of training data. Augmentation should only be done on the training set, never on the validation set.

 

###Normalisation: Refers to rescaling the pixel values so that they lie within a confined range. One of the reasons to do this is to help with the issue of propagating gradients.

 

 

##Network building
Choosing the architecture: For this demo, we used the 'ResNet' architecture. Its biggest upside is that the 'skip connections' mechanism allows very deep networks.

 

###Ablation Experiments: These refer to taking a small chunk of data and running your model on it - this helps in figuring out if the model is running at all.

 

###Overfitting on Training Data: This tells you whether the model is behaving as expected or not.

 

###Metrics: Depending on the situation, we choose the appropriate metrics. For binary classification problems, AUC is usually the best metric.

 

###Hyperparameter tuning: We tune hyperparameters such as the learning rate, augmentation of images, batch size, etc. Also, we only change the architecture of the network if we have already tried tuning all other hyperparameters.
