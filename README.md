# Creating-Variational-AutoEncoders-from-scratch

The implementation was inspired by the following paper : "Auto-Encoding Variational Bayes" (https://arxiv.org/abs/1312.6114)

Autoencoders are neural networks which try to recreate a given input by using two set of networks namely an encoder and a decoder. The encoder converts the given input into a lower dimensional representation (called the bottleneck).The encoder output is then fed into mean and standard deviation vectors. This lower dimensional representation is also called the latent vector. The decoder then uses this lower dimensional representation to recreate the initial input vector. The objective is to learn the initial input representations when trying to map them back to the original dimensions.

![vae](https://github.com/madarshb19/Creating-Variational-AutoEncoders-from-scratch/assets/70708225/6dcadf5b-eb9c-48bc-b9bf-c783a3291b10)


Variational AutoEncoders are a special type of autoencoders where the latent vector takes into input the mean and standard deviation vectors randomly sampled from a Gaussian distribution. As it is difficult to perform backpropagation when coefficients are randomly sampled,we use the reparametrization trick where instead of randomly sampling the mean and standard deviations,we find the new reparametrized latent vector as : z = mu + sigma * epsilon where epsilon represents the stochastic term following a standard normal distribution (epsilon ~ N(0,1)).

<img width="850" alt="vae_actual" src="https://github.com/madarshb19/Creating-Variational-AutoEncoders-from-scratch/assets/70708225/1cf85901-c404-43e4-96f9-7f53b96427af">


The loss function is computed as follows : L = contrastive loss + KL Divergence. The contrastive loss represents the similarity between the input image and the output image and KL divergence ensures that the sampling is close to the standard normal distribution.

![loss1](https://github.com/madarshb19/Creating-Variational-AutoEncoders-from-scratch/assets/70708225/7d748f8f-6986-4d33-aecf-50785c764bdc)

We have implemented the Variational AutoEncoders to learn MNIST datasets.
