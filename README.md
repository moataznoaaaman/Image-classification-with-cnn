# Action detection from Egyptian movies with CNN 

## Problem definition 
With its diversity and importance in the MENA region and the whole world, Egypt is considered the Hollywood of the MENA region. The comes from the fact that it was the first arab country to make movies and its movie industry extends to over 100 year with A class movies and actors. But with the rich and diverse culture of Egypt, sometimes it may be hard for non-egyptians to understand the context of the scens. this is because egyptian movies scens dosent only depend on the dialoge, but it also depend on the rich cataloge of body language that the egyptians may offer. to overcome this problem, a manual extraction and annotation of images from movies were used along with a CNN to try to annotate the body language in the upcoming movies. 

## Data

The data used for developing the model was gathered manually by the whole class students where each project group has to give a number of images that is proportional to the number of students in the group. since i was working alone i was supposed to provide 1000 image to one of our classification classes which was group talking. fortunately i provided the class and additional 1000 images for the pair talking class. the criteria for the images is that each image had to be keyfram images to avoid using the same images over and over which will give poor results. 

## Images preprocessing
All the images were are originally 640 x 480 x 3. the first preprocessing step done was to rescale the images from their original size to 50 x 50 x 3 to reduce the number of trainable parameters. the second step for the images was to normalize the pixels to fall between 0 and 1.


### Model architecture
The CNN model is similar to the architecture of AlexNet with the necessary modifications to be able to process the RGB images of our dataset. the model consists of 3 Convolutional layers and 3 maxpooling layers and a final fully connected layer. 
the architecture goes as follows : 
* A Convolutional layer with kernal size of 3 x 3 and stride = 1. the output feature map has a depth of 48. a RELU activation function is then applied
* A maxpooling layer with a kernal of 2 x 2 and a stride of 2

* A Convolutional layer with kernal size of 5 x 5 and stride = 1. the output feature map has a depth of 96. a RELU activation function is then applied
* A maxpooling layer with a kernal of 2 x 2 and a stride of 2 

* A Convolutional layer with kernal size of 7 x 7 and stride = 1. the output feature map has a depth of 144. a RELU activation function is then applied
* A maxpooling layer with a kernal of 2 x 2 and a stride of 2 

* The outout of the last layer is then feed to the fully connected layer. this layer consists of 2 layers, input, and output layers. 

* The input layer consists of 72 neurons and its followed by a sigmoid activation function 
* The output layer consists of 10 neurons and it is followed by a softmax activation function

* The weights of the model were randomally initalised from a normal distribution

* The objective function is CrossEntropyLoss

* The optimization function is Adam optimizer

## Hyperparameters
 * The number of Epoch is 70
 * the batch size is 5
 * the learning rate is 0.0005


## Results and performance 
The model was tested on 2 datasets. the first dataset was the one i gathered which was 2000 of group and pair talking. the second dataset was the the whole classes that was given by the group effort. 

* for the first dataset the accuracy of the model could not exceed 90 % regardless of the hyperparameters setup 
* for the second dataset the model could not exceed 70% regardless of the setup. this may come from the quality of the dataset as some groups dident stress on the photos quality or dident stress on the selection of photos from key frames. This should result in a poor data quality and hence poor model. 
