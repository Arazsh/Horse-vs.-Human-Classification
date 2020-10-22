# Horse vs. Human Classification with VGG19 

In this code, a model is developed to classify images into two classes of horse and human. This model benefits from the convolutional layesrs of VGG19 neural netwok, which is trained by over one million images of ImageNet dataset for 1000 classes. The dataset used in this code consists of 1283 horse and human artificial images of 300×300 pixels. The dataset is constructed by Laurence Moroney and is available at Kaggle. As the dataset is relatively small, it is less likely to be able to well train the convolutional layers of a CNN using this dataset. Therefore, to enhance the acuracy of the model in this code, the convolution block of VGG19, which is well trained by ImageNet dataset, is extracted and installed in our model. The convolutional layers are freezed and only the dense layers of the model are trained by the horse and human images. The model shows the accuracy of over 95% for validation data of the same dataset, which are artificial images. Also, the model shows relatively high accuracy for out of dataset images regarding the limited number of training images and the high similarity between them.

## Downloading the dataset

The dataset used in this code is available in Kaggle and is constructed by Laurence Moroney. Here, the two direct links for train and validation data that are provided by Laurence Moroney (lmoroney@gmail.com / laurencemoroney.com) are used to download the images into the notebook.  
[Train data](https://storage.googleapis.com/laurencemoroney-blog.appspot.com/horse-or-human.zip)  
[Validation data](https://storage.googleapis.com/laurencemoroney-blog.appspot.com/validation-horse-or-human.zip)  

![alt text](https://github.com/Arazsh/Horse-vs.-Human-Classification/blob/media/image1.png?raw=true)  

The above figure demonstrates two random horse and human images from the train dataset. Also, the number of train and validation images are provided at the top of the figure.  

## ImageDataGenerator

The next section of the code employs ImageDataGenerator and flow_from_directory to generate the train and test data for the model that is going to be built. To improve the accuracy of the model and to reduce the overfitting issue, image augmentation was tested for training set. However, the model predictions were weaker by using image augmentation and I commented out that part of the code. 

## VGG19
Since the number of training images in the dataset is low (1027), it is unlikely to be able to well train the convolutional layers of a model using this dataset. To tackle this problem, Transfer Learning and VGG19 are used. As can be seen in the code, the VGG19 from Keras applications is called and it is loaded with ImageNet weights. ImageNet contains over one million images in 1000 classes which delivers a well-trained filter bank for the VGG19. I also freezed the VGG19 layers to prevent the convolutional layers from changing while training our model that uses the filter bank of VGG19.  


## Constructing the model

For constructing the convolutional layers of the model, I utilized the filter bank of VGG19 from the second layer to the fourth convolutional layer of the fifth block 'block5_conv4' (top layer is excluded and substituted with a layer to accommodate 150*150 images). In the following of the filter bank, a fllatening layer in addition to four Dense layers are accumulated. RMSprop and binary_crossentropy are then used for optimizer and loss function. The model is then trained for 30 epochs and the accuracy of 0.9688 is obtained for the validation set, that can be seen in the notebook. Furthermore, the myCallback class and callbacks instance object are defined before fitting the model to have control over the number of epochs the fitting runs based on train and validation accuracies.

## Testing the model for images out of dataset

As can be seen in the above figure, the dataset images are computer created. To test the model for images out of the dataset that can include natural images, a section in the notebook is provided to upload images and predict if they belong to horse or human class. I tested the model for random horse and human images with different sizes and various contents like paintings or photo of toys. The model shows acceptable accuracy considering the number of training images and the high similarity among them.

## Access to filtered images 

At the end of the notebook, a piece of code is provided to get access to filtered images in the model's filter bank including the convolutional layers. Below, we can see the results for a random image and the first few layers. Following the code, it is possible to obtain the output of any specific filter in any desired layer. 

![alt text](https://github.com/Arazsh/Horse-vs.-Human-Classification/blob/media/image2.png?raw=true) 

