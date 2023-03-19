
**Introduction:** <br>
One of the complicated tasks in medical imaging is to diagnose MRI(Magnetic Resonance Imaging). Sometimes to interpret the scan, the radiologist needs different variations of the imaging which can drastically enhance the accuracy of diagnosis by providing practitioners with a more comprehensive understanding.
 
 
But to have access to different imaging is difficult and expensive. With the help of deep learning, we can use style transfer to generate artificial MRI images of different contrast levels from existing MRI scans. This will help to provide a better diagnosis with the help of an additional image.
 
In this capstone, we will use CycleGAN to translate the style of one MRI image to another, which will help in a better understanding of the scanned image. Using GANs we will create T2 weighted images from T1 weighted MRI image and vice-versa.

Problem statement: To build a Generative adversarial model(modified U-Net) which can generate artificial MRI images of different contrast levels from existing MRI scans.

**Project pipeline**<br>
The project pipeline can be briefly summarized in the following four steps:
•	Data Understanding: Here, we need to load the data and create the dataset for it.
•	Image Processing: In this step, we will have to process the images using different steps.
•	Model-Building and Training: This is the final step at which we have to create our Generators and Discriminators using a modified U-Net architecture(similar to CycleGAN). We also have to define the loss function and training step for model training.


