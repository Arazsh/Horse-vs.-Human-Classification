# Horse-vs.-Human-Classification

In this code, a model is developed to classify images into two classes of horse and human. This model benefits from the convolutional layesrs of VGG19 neural netwok, which is trained by over one million images of ImageNet dataset for 1000 classes. The dataset used in this code consists of 1283 horse and human artificial images of 300×300 pixels. The dataset is constructed by Laurence Moroney and is available at Kaggle. As the dataset is relatively small, it is less likely to be able to well train the convolutional layers of a CNN using this dataset. Therefore, to enhance the acuracy of the model in this code, the convolution block of VGG19, which is well trained by ImageNet dataset, is extracted and installed in our model. The convolutional layers are freezed and only the deep layers of the model are trained by the horse and human images. The model shows the accuracy of over 95% for validation data of the same dataset, which are artificial images. Also, the model was tested for 30 natural random images of horses and humans with various sizes, and the acuracy of around 80% was observed.

## Downloading the dataset

The dataset used in this code is available in Kaggle and is constructed by Laurence Moroney. Here, the two direct links for train and validation data that are provided by Laurence Moroney (lmoroney@gmail.com / laurencemoroney.com) are used to download the images into the notebook.
[Train data](https://storage.googleapis.com/laurencemoroney-blog.appspot.com/horse-or-human.zip)
[Validation data](https://storage.googleapis.com/laurencemoroney-blog.appspot.com/validation-horse-or-human.zip)
