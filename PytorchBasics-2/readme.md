## Fashion MNIST 

This dataset consists of 28X28 greyscale images.

1. Import nn and Optim packages
2. Define Network Architecture (Input, Hidden, Output Layers and Forward Pass(consists of ReLU and Softmax))
3. Create Model, Optimizer--SGD/Adam and Criterion (NLLLoss)
4. Train the Network (Using for loops, epochs --> Calculate logits,do backward pass and optimizer step)

### Points to Remember

NLLLoss vs CrossEntrophyLoss

SGD Vs Adam

1. Build a Model on Fashion MNIST and try minimizing the loss of the model 
```
for e in range(epoch):
    running_loss = 0   ###tracking loss
    for image,label in trainloader:
        logps = model(image)
        loss = criterion(logps,label)
        optimizer.zero_grad() ##zeroing grad
        loss.backward()  ##doing backward to find gradients
        optimizer.step()
        running_loss +=loss.item()
  ```
 2. Inference 
 
 Build a model using trained data and test it on the test data (see whther it overfits or underfits)
