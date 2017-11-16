# Traffic Sign Classifier

### Network Architecture

- Convolutional layer 1 (Input = 32x32x3. Output = 28x28x6)
- Activation function – ReLU
- Max Pooling (Input = 28x28x6. Output = 14x14x6)
- Convolution layer 2 (increased depth of filter from 16 to 32 which greatly increased accuracy)
- Activation function – ReLU
- Max Pooling (Input = 10x10x32. Output = 5x5x32)
- Flattening (due to change in convolutional layer 2 above this is flattened to 800 instead of 400)
- Fully connected layer 1 (Input = 800. Output = 120)
- Activation function – ReLU
- (Attempted dropout – later removed due to greatly decreases accuracy and validation set)
- Fully connected layer 2 (Input = 120. Output = 84)
- Activation function – ReLU
- Fully connected layer 3 (Input = 84. Output = 43)

The architecture used is largely unchanged from the provided LeNet architecture. The major change was with changing the depth of the filter in the second convolutional layer from 16 to 32 which resulted in the network achieving ~96% accuracy on the validation set and ~70% on my own images downloaded from the internet. With that result my main concern was with the model “overfitting” the training data. To address this I attempted to implement a dropout layer but so resulted in really bad accuracy against the validation set (~70%) and additional images downloaded from the internet (~55%). 

### Data Preprocessing 

For preprocessing of the data, I normalized the data, as this is the format that tends to perform the best in neural networks, but chose not to convert the images to grayscale as the colors in the images may be highly pertinent to accurately classifying a given sign. Additionally the data was shuffled to get a more random distribution of different types of signs in the training and validation sets.

### Performance

The relatively poor performance of the model against un-seen data (despite a high accuracy against the validation set) could be attributed to a number of different causes. First, the training set is very un-balanced meaning that it may “favor” classifying to some images over others. This could be addressed by augmenting the dataset – either with more “raw” data or by manipulating the provided data (shading, transforming, etc.) and adding them to the dataset to provide a more “balanced” dataset. Effectively adding a drop-out layer should, theoretically, help to reduce over-fitting but I did not find that to be the case with my testing. Additionally, some pre-processing of the incoming images to make them “look” more like the images in the dataset could help. 

The number of epochs and batch sizes were kept at 10 and 128, respectively; I found that increasing the number of epochs did not affect the accuracy and started to “stall” after a certain point even when testing with the drop-out layer in place. 






