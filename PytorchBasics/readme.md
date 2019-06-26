
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

We adjust these **network parameters** and minimize the loss which is done by using **Gradient Descent**. 
Gradient points to direction of fastest chage and maximizes the loss

![image](https://user-images.githubusercontent.com/12963112/59560201-a627ac00-8fd3-11e9-9f37-8adc152acc50.png)

## BackPropogation

1. Forward Pass for calculating **LOSS**
2. Backward pass for calculating **Gradient Descent**
3. These steps are done MULTIPLE TIMES

## Losses in Pytorch 
##### Cross Entrophy Loss : **nn.CrossEntrophyLoss()**

```criterion = nn.CrossEntropyLoss()
logits = model(images)  **_We get logits from the model_**
loss = criterion(logits, labels) **_calculating loss through logits_**
```
**For Negative Log Likelihood we use _nn.LogSoftmax_**.  **nn.LogSoftmax** gives us the **actual probabilites** in a model by taking exponential values
''' 1. dim = 0 ( calculates softmax across rows ) 
''' 2. dim = 1 ( calculates softmax across columns where each row sums to 1) In our example of MNIST each row is one of our examples so we make sure that we calculate our loss in each of the examples

## How to perform **BACKPROPOGATION** automatically?

## AUTOGRAD

1. Pytorch **keeps track** of all operations you do on tensors
2. requires_grad = "Yes" --> Tells pytorch to keep track of all operations of that particular tensor on which you enabled it
3. tensor_name.**grad_fn** gives the type of function implemented on tensor
4. **torch.set_grad_enabled**(True|False) for the global setting of gradients enabling or disabling

### How to implement and how its useful?

1. Loss depends on **weights** and **bias** parameters 
2. we do Forward pass to calculate **loss** then with the loss we do backward pass and obtain **gradients** for our weights. With these gradients we do gradient descent step.

We have to update these weights after every step of backward pass because you do these steps multiple times (epochs)  . **How ?**

1. **OPTIMIZERS**  --> from torch import **optim** --> optim.SGD() / optim.Adam() etc.,
2. **optimizer.zero_grad()** --> cleans all gradients

### Steps to implement loss,backward/fwd pass,autograd etc in a Program

1. Craeye Model, Intilatize criterion using Loss and optimizer
2. Run a forloop with epochs in which you flatten your images
3. Inthat set optimizer gradients to zero at the start of each loop (for updating new gradients)
4. Calculate logits/logps and pass them in criterion function to calculate loss
5. Now do optimizer.step() for updating new gradients calulated

