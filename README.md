# W251 Homework 4
#### Greg Tozzi

## ConvnetJS MNIST demo

### 2.1 - Name all the layers in the network, describe what they do.

- The *input layer* accepts the 24 x 24 images.
- The *first convolutional layer* applies eight 5 x 5 filters to the input image.  Setting `pad:2` adds two pixels of padding to the input, effectively increasing the image over which the filters are applied to 28 x 28 pixels.  The output of this layer is a 24 x 24 x 8 tensor.
- The *first pooling layer* reduces the dimensionality of the output of the previous layer by by taking the maximum value returned by the convolutions.  The output of this layer is a 12 x 12 x 8 tensor.
- The *second convolutional layer* applies 16 5 x 5 filters to the output of the first pooling layer. This layer applies a padding of two pixels around the input. The resulting output is 12 x 12 x 16.
- The *second pooling layer* reduces the dimensionality of the output of the previous layer to 4 x 4 x 16.
- The *softmax* layer takes the input of the previous layer and outputs a 10-element vector, the values of which give the estimated probability of the input being of each of the 10 possible classes.

### 2.2 - Experiment with the number and size of filters in each layer. Does it improve the accuracy?

The baseline model's validation accuracy appears to converge to 0.94.  I ran the following experiments:

- *Double the filters in the first convolutional layer.*  The validation accuracy converged a bit lower than in the baseline example (approximately 0.93).
- *Halve the filters in the first convolutional layer.*  The validation accuracy converged to approximately 0.97.
- *Double the filters in the second convolutional layer.*  The validation accuracy converged to 0.99.
- *Halve the filters in the second convolutional layer.*  The validation accuracy converged to 0.95.

### 2.3 - Remove the pooling layers. Does it impact the accuracy?
No.

### 2.4 - Add one more conv layer. Does it help with accuracy?
Possibly.  Adding another 16-filter convolutional layer resulted in validation accuracy converging to 0.99.

### 2.4 - Increase the batch size. What impact does it have?
Training slows a bit, and validation accuracy converged to around 0.92.

### 2.5 - What is the best accuracy you can achieve? Are you over 99%? 99.5%?
I'm right around 0.99.
