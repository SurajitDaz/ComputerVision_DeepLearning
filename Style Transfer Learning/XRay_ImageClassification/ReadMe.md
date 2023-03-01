## Dataset: https://drive.google.com/file/d/1f4PX0sS2xasRKDXbtXnPW060Eb1Kfd2t/view

# Summary
Following are the main concepts you learnt in this project:

 

## Data preprocessing
Augmentation: Because this is a specific industry use-case, we put constraints of the augmentations that we can or cannot do (e.g. no vertical flipping). Also, we ensure that augmentation is only done on the training data.

 

### Resizing: 
We need to be careful while resizing images. The two most common ways to resize images are to 1) crop and 2) to resize by 'averaging' the pixels (similar to pooling). The risk of cropping is that you lose some pixels, while the risk of resizing by averaging is that the finer edges etc. may be lost. Since in most realistic problems you have to reduce the image size (to meet computational constraints), you should choose between these two carefully. If you do not care about finer edges etc. (e.g. when coarse-grained features will suffice), you can do averaging. If you care about finer features but only a central region of the image, you can use cropping.

 

### Normalisation: 
We usually normalise using a min-max range. Make sure to not divide by 255 blindly since all images (such as X-Ray scans) don't necessarily have the range 0-255.

 

## Network building:
### Architecture: 
We used a ResNet together with a decaying learning rate and a weighted cross-entropy loss (to account for class imbalance). We used AUC as the metric. 

 

### Metrics: 
While choosing a metric for medical images with a prevalence problem, we pick recall over precision. We don't want to miss out on any cases of effusion. In any case, working with AUC and a manual threshold is the best option.

 

### Weighted Cross-entropy: 
This loss is used when the error in one direction is costlier than the other, for example, it is much more undesirable to diagnose 'effusion' as 'normal' than the other way around. This is done by assigning 'higher weights' to the errors in certain classes.
