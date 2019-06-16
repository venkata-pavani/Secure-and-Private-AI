# Secure-and-Private-AI
Learning Different Privacy Techniques in Deep Learning using Python

### Lesson 1

`` torch Library is the part of python packages ''

### Functions Used  

1. randn(a,b)  -- for generating random numbers of shape (a,b)
2. randn_like(input) -- to generate random numbers of shape like input
3. torch.sum(a,b) -- performs summation of a  and b just like numpy
4. torch.mm(a,b) -- performs multiplication of a and b 
5. k.reshape(a,b) -- creates a new tensor with same data of k and size (a,b) . The cloning operation is done in different part of memeory 
6. k.resize_ -- returns the same tensor of different shape but there will be be some loss of data in tensor the memory hold the original data
7. k.view -- returns a new tensor with same data of k and size (a,b)
8. torch.from_numpy(vector_name) -- converts numpy array into torch

## Learning Gradient Descent, Forward Propogation, BackPropogation (Check notebook for equations and detailed explanations)

In MNIST dataset we pass images through Neural Network and enable it to predict images with higher probability

## GradientDescent

Goal: Minimize the Loss so as to make better prediction of numbers better (i.e, maximizing the propbability)

### *How?*

We adjust these network parameters and minimize the loss which is done by using **Gradient Descent**. 
Gradient points to direction of fastest chage and maximizes the loss

[[image](https://user-images.githubusercontent.com/12963112/59560187-6f519600-8fd3-11e9-82b0-fa121df959d9.png](url)

## BackPropogation

Through forward pass we calculate the loss and then we pass that backward again and then get the gradient for weights and update these weights.
Then we do a forward pass and get the loss and then do backward pass to get gradients for weights and update these weights and so on..

### Losses in Pytorch
##### Cross Entrophy Loss
**nn.CrossEntrophyLoss()**

criterion = nn.CrossEntropyLoss()
logits = model(images)  **_We get logits from the model_**
loss = criterion(logits, labels) **_calculating loss through logits_**


**For Negative Log Likelihood we use _nn.LogSoftmax_**.  **nn.LogSoftmax** gives us the actual probabilites in a model by taking exponential values
1. dim = 0 ( calculates softmax across rows ) 
2. dim = 1 ( calculates softmax across columns )
