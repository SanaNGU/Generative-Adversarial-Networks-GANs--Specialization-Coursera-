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


## Week 2
#### In the Second week of the first course you will be Learn :
- Deep Convolutional GANs
- ---
- ---

## Week 3
#### In the Third week of the first course you will be Learn :
- Wasserstein GANs with Gradient Penalty
- 

## Week 4
#### In the last week of the first course you will be Learn :
- Conditional GAN & Controllable Generation
