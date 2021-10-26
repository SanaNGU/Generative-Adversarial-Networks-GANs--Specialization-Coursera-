# Course 1 :Build Basic Generative Adversarial Networks (GANs)
## Week 1
#### In the first week of the first course you will be Learn :
- What is GAN and where we can use it?
 GANs allow you to build models that can generate realistic images or music and other things,GANs comprises of two models thatcompete with each other and reach a point where realistic examples are produced by the generator.
 
- What are the two models behind GANs?
Generator and discriminator (both are neural networks)

- GAN application; see some not- -existent people who generate by GAN!!!
<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/GAN1.png" alt="drawing" style="width:100px;"/>
<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/GAN2.png" alt="drawing" style="width:100px;"/>
You can try it yourself using this link: https://www.thispersondoesnotexist.com/

 -  Intuition Behind GANs
 -  
 - Quick look at the generator and the discriminator in GANs
 - 
   **The Discriminator** is a classifier that learns the probability of class Y(real or fake)given feature X (conditional prob.)and these probabilities  are the feedback for the generator 
   **The Generator** is the heart in GANs,the generator the  produces fake data that tries to look real, it learns to mimic that distribution of features  X from the class od your data and in order to produce different outputs each time it takes random features as input
   - putting all together :
  
  **The discriminator** looks at real and fake images over time, makes guesses, and gets feedback on whether its guess was right or wrong.Over time, it learns to discern real from fake better, but note that since the generator is also learning, the fake images get more realistic and harder to discern. This cat and mouse game enables both models to learn in tandem. 
 
 With feedback from the discriminator on whether a fake image looks real or fake, **the generator** starts producing fake images that are more and more realistic (that tries to fool the discriminator). Images that look “fake” to the discriminator are discarded in favor of those that look “real” to the discriminator; since the discriminator is improving over time as it sees more reals and fakes, the generator needs to continually learn too.

- Finally, a quick look to Pytorch
### The practial task for week 1 is filling missing code lines while building and training a GAN that can generate hand-written images of digits (0-9),
here is the generated output shoud be looked like in the first run: 

<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/GAN3.png" alt="drawing" style="width:400px;hight=300"/>


here is the generated output shoud be after the training: 

<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/GAN4.png" alt="drawing" style="width:400px;hight=300"/>


## Week 2
#### In the Second week of the first course you will be Learn :
- Deep Convolutional GANs:A DCGAN is a direct extension of the GAN, except that it explicitly uses convolutional and convolutional-transpose layers in the discriminator and generator, respectively.
- ---
- ---
#### -As an optional reading suggestion by the course, the paper behind the deep convolutional GAN (DCGAN) was a nice thing to explore
'Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks (Radford, Metz, and Chintala, 2016)',I summarised the important points from that paper  here:
/*:
  - Gap:Gan have been known to be unstable to train, hard to understand what GANs learn  
  - paper contribution: propose an arch. topology convolution GAN that make more stable to train GANs
  - Very useful to learn unsupervised image representations(Using the features learnt by generator for classification tasks. Performs better than all k-means extracted features)
  - visualize the filters learnt by GANs (Disc. part) using guiged BP 
  - Implement nice vector arithmetic  properties 
 
 
 ### Then we come to the architectur that the paper has used:
 
 
  - All the pooling layers are replaced with strided convolutions in the discriminator and fractional strided convolutions in the generator (allowing the network to learn its own downsampling )
  - No fully-connected on. the top of the Conv featue and replace it with global average pooling (remove fully connecting hidden layers) (eliminating all fully connected layers on top of convolutional features. Even for the last layer, the convolution layer is flattened and fed into a single sigmoid output.)
  - Batchnorm used in both Generator and Discriminator
  - ReLu activation is used for the generator for all the layers except the last layer which uses tanh
  - Discriminator uses LeakyReLu for all the layers.  
  - Hyperparameterw: Minibatch SGD with minibatch size of 128, Weights initialized with 0 centered Normal distribution with standard deviation = 0.02, Adam Optimizer, Slope of leak = 0.2 for LeakyReLU., Learning rate = 0.0002, β1(momentum term ) = 0.5
 */

The discriminator architecture is same as that of a normal image classification model.is made up of Convolution layers, Activation layer and BatchNormalisation(In the DCGAN paper, strides are used instead of pooling to reduce the size of a kernel. Also, there is no Fully Connected layer in the network. Leaky ReLU with leak slope 0.2 is used.) The input is a 3x64x64 input image and the output is a scalar probability that the input is from the real data distribution. 


The generator is comprised of convolutional-transpose layers, batch norm layers, and activation layer(If the layer is not the last layer then ReLu activation is applied else Tanh).
The input is a latent vector, zz, that is drawn from a standard normal distribution. First channel size is 1024 which is then decreased block by block to 3 for RGB image. Finally, we will get a 3x64x64 Tensor which will be our image. The strided conv-transpose layers allow the latent vector to be transformed into a volume with the same shape as an image. In the paper, the authors also give some tips about how to setup the optimizers, how to calculate the loss functions, and how to initialize the model weight.
<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/DCGAN.png" alt="drawing" style="width:600px;hight=400"/>


The Discriminator wants to predict the fake images as fake and real images as real. On the other hand, the Generator wants to fool Discriminator into predicting the fake images produced by the Generator as real.
### Then Finally, the practial task for week 2 is filling missing code lines while building and training a CGGAN that can generate hand-written images of digits (0-9),
here is the generated output shoud be looked like in the first run: 

<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/GAN6.png" alt="drawing" style="width:400px;hight=300"/>


here is the generated output shoud be after the training: 

<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/GAN7.png" alt="drawing" style="width:400px;hight=300"/>

you can see how DCGAN is generating more 'real' looking images than GANs with the fully connected network

## Week 3
#### In the Third week of the first course you will be Learn :
- Wasserstein GANs with Gradient Penalty

### Then Finally, the practial task for week 3 is filling missing code lines while building and training a WGAN-GP to solve some of the stability issues with the GAN
In this code, since the changes for WGAN-GP are done to the loss function during training, I will reuse the previous GAN code for the generator and critic class.one note to keep in mind: In WGAN-GP, we no longer use a discriminator that classifies fake and real as 0 and 1 but rather a critic that scores images with real numbers(no need for the Sigmoid layer at the output).


here is the generated output shoud be looked like in the first run: 

<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/before training.png" alt="drawing" style="width:400px;hight=300"/>


here is the generated output shoud be after the training: 

<img src="https://github.com/SanaNGU/Generative-Adversarial-Networks-GANs--Specialization-Coursera-/blob/main/Course1%20:Build%20Basic%20Generative%20Adversarial%20Networks%20(GANs)/images/after training.png" alt="drawing" style="width:400px;hight=300"/>

you can see how DCGAN is generating more 'real' looking images than GANs with the fully connected network
## Week 4
#### In the last week of the first course you will be Learn :
- Conditional GAN & Controllable Generation
