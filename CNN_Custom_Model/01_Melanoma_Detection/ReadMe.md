# Abstract:
Melanoma is a type of cancer that can be deadly if not detected early. It accounts for 75% of skin cancer deaths. A solution which can evaluate images and alert the dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis. In this multiclass classification problems, no pre-trained model using Transfer learning is used. All the model building processes are based on the approach of the custom model.

# Problem statement:
The project is about to build a multiclass classification model using a custom convolutional neural network in TensorFlow so that it can accurately detect melanoma.

# Dataset: 
https://drive.google.com/file/d/1xLfSQUGDl8ezNNbUkpuHOYvSpTyxVhCs/view
The dataset consists of 2357 images of malignant and benign oncological diseases, which were formed from the International Skin Imaging Collaboration (ISIC). All images were sorted according to the classification taken with ISIC, and all subsets were divided into the same number of images, with the exception of melanomas and moles, whose images are slightly dominant.
The data set contains the following diseases:

Actinic keratosis
Basal cell carcinoma
Dermatofibroma
Melanoma
Nevus
Pigmented benign keratosis
Seborrheic keratosis
Squamous cell carcinoma
Vascular lesion
 
# Project Pipeline
Data Reading/Data Understanding → Defining the path for train and test images 
Dataset Creation→ Create train & validation dataset from the train directory with a batch size of 32. Also, make sure you resize your images to 180*180.
Dataset visualisation → Create a code to visualize one instance of all the nine classes present in the dataset 

# Model Building & training: 
Creating a CNN model, which can accurately detect 9 classes present in the dataset. While building the model we rescale images to normalize pixel values between (0,1).
Sellecting an appropriate optimiser and loss function for model training
The model is trained for ~20 epochs
Keeping records of all findings after the model fit, watching if there is evidence of model overfit or underfit
Choosing an appropriate data augmentation strategy to resolve underfitting/overfitting 

# Model Building & training on the augmented data:
Creating a CNN model, which can accurately detect 9 classes present in the dataset. While building the model we rescale the images to normalize pixel values between (0,1).
Sellecting an appropriate optimiser and loss function for model training
The model is trained forf ~20 epochs
Findings are written after the model fit, see if the earlier issue is resolved or not?

Class distribution: We examine the current class distribution in the training dataset 
- Which class has the least number of samples?
- Which classes dominate the data in terms of the proportionate number of samples?

Handling class imbalances: Rectify class imbalances present in the training dataset with Augmentor library.

Model Building & training on the rectified class imbalance data :
Creating a CNN model, which can accurately detect 9 classes present in the dataset. While building the model we rescale images to normalize pixel values between (0,1).
Choosing an appropriate optimiser and loss function for model training
Tthe model is trained for ~30 epochs
The findings are noted after the model fit, We observe if the issues are resolved or not?

