**Dataset:**<br>
The inbuilt dataset in TensorFlow, which returns train_images and train_labels as the first tuple. The second tuple contains the test set, which is not here. Link: [TensorFlow official documentation ](https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist/load_data)

**Project Pipe Line:** <br>
DCGAN implementation can be divided into six steps. They are as follows (Ref. manual for implementation https://www.tensorflow.org/tutorials/generative/dcgan):<br>

* Importing Libraries with the specific versions
  - numpy - 1.19.2

  - tensorflow - 2.4.1

  - matplotlib - 3.3.2

  - skimage - 0.17.2

* Data Loading and Visualisation

* Data Preprocessing
  - **Step-1 Image normalization:** We normalize the image pixels in range (-1, 1) using the following formula. Dividing raw pixel values of range (0, 255) by 127.5 will make it in the range (0, 2) and when we subtract 1 from all the values, we get (-1, 1).
  - **Step-2 Resizing Image:** Here, we first normalised the data between [-1, 1] for faster training, then , resized images to [32, 32] and added another dimension as an image channel using an inbuilt function in skimage library (https://scikit-image.org/docs/dev/api/skimage.transform.html#resize). 
  - **Step-2 Batch/Suffle** We batch and shuffle the dataset. Refer to [this](https://www.tensorflow.org/api_docs/python/tf/data/Dataset#batch) for batch and [this](https://www.tensorflow.org/api_docs/python/tf/data/Dataset#shuffle) for the shuffle.

 
* Model Building:
  - GAN is composed of two components - the generator and the discriminator. We can build a generator that uses deep convolution networks in the background. In order to build the generator conv 2d transpose (reverse CNN) layer has been used. It takes 1-dimensional input (i.e. noise) and progressively increases the height and width of the chanel. Also, here deep convolutional layers are used in upsampling the data. 
  - **Building Generator:** We use the following inbuilt Keras layer to implement the [Transposed 2D Convolution](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Conv2DTranspose).  There prototype of the Trnasposed 2D CNN looks like below: ![Trnsposed2D CNN Archite](https://user-images.githubusercontent.com/75905023/226161503-bd78a6f1-4e90-48da-993b-bfa9bfe6dd64.jpeg)

  - After Implementation, let’s visualise the model we have built using the [plot_model function](https://www.tensorflow.org/api_docs/python/tf/keras/utils/plot_model). 
  - **Building Discriminator:** Custom Model built up with an out '0' or '1'.
  - **Loss calculation for Discriminator:** Using [binary cross-entropy](https://www.tensorflow.org/api_docs/python/tf/keras/losses/BinaryCrossentropy) as a loss function, loss is calculated. It involves two cases for loss computation, wherein one is associated with the real input image and the other is a fake input image produced by the generator
  real_loss = cross_entropy(tf.ones_like(real_output), real_output)<br>
  fake_loss = cross_entropy(tf.zeros_like(fake_output), fake_output)<br>
  total_loss = real_loss + fake_loss<br>
  The generator has only one situation where it needs to improve, which is when it fails to fool the discriminator. Since the generator calculates its loss from the discriminator, it also uses binary cross-entropy loss. cross_entropy(tf.ones_like(fake_output), fake_output)<br><br>
* Optimizing the Loss:<br>
  After calculating the losses, we need to ensure the initialisation of the optimisers for weight updation of the models. We will also initialise the checkpoints to save the weights of our models to use in the subsequent steps of training. We use [adam](https://www.tensorflow.org/api_docs/python/tf/keras/optimizers/Adam) optimizers for both the components of GAN. 
* Model Training:<br>
  - A custom fucntion has been used to train the models for an estimated number of epochs. There are two major steps in training any deep learning model - the first one is calculating the loss and the second one is updating the weight and bias of the model using the optimizer. We initialise the [gradient tapes](https://www.tensorflow.org/api_docs/python/tf/GradientTape) for the generator and discriminator for auto calculation of gradients. It is accomplished by the following code using tf.GradientTape() as gen_tape, tf.GradientTape() as disc_tape
  - Now the next remaining step in the training is to calculate and apply the gradients on the model using the loss we just calculated.
  - To calculate the gradients we just need to call the gradient tape functions, we initialised earlier. For example, we call the following method for the generator. [Reference](https://www.tensorflow.org/api_docs/python/tf/keras/optimizers/Optimizer). gen_tape.gradient(gen_loss, generator.trainable_variables). After calculating the gradients we also need to apply the gradients on the optimizers to update the model’s weight and biases.  generator_optimizer.apply_gradients(zip(gradients_of_generator, generator.trainable_variables)) In the next video, you will understand that you just need to call the function that you created earlier to perform one batch of training. It provides us with better comprehension and easier code management. 

We train our model for a certain number of epochs. For each epoch, we have several batches of images, which we pass through training flow one by one. Note that we are calling the train_step function we defined in the previous step.


for epoch in range(1, EPOCHS+1):    

   - for image_batch in train_dataset:

       - train_step(image_batch)


* Generating a GIF of Generated Images
