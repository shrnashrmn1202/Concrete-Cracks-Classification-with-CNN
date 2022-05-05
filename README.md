# Cracks-Classification-with-CNN

## Identifying Cracks on Concrete with Image Classification using Convolutional Neural Network

A Convolutional Neural Network model is created to identify cracks on concrete with high accuracy. 
The problem is modelled as a binary classification problem: image with no cracks (negative) and image with cracks (positive). The model is trained with a dataset of 40000 images (20000 images of concrete in good condition and 20000 images of concrete with cracks).

![image](https://user-images.githubusercontent.com/100325884/166852314-9adb210a-d3ab-4a5d-a663-6ca6e4641234.png)


The dataset with all the images used in this project was downloaded from Mendeley Data:
Özgenel, Çağlar Fırat (2019), “Concrete Crack Images for Classification”, Mendeley Data, v2 DOI: 10.17632/5y9wdsg2zt.2

## IDE and Framework
This project is created using Sypder as the main IDE. The main frameworks used in this project are Numpy, Matplotlib, and TensorFlow Keras.

## Methodology
The methodology for this project is inspired by a documentation on the official TensorFlow website. The link to refer to: https://www.tensorflow.org/tutorials/images/transfer_learning

### 1. Data Preprocessing
The image data are loaded along with their corresponding labels. 

### 2. Data Pipeline
The data is first split into train-validation set, with a ratio of 70:30. The validation data is then further split into two portion to obtain some test data, with a ratio of 80:20. The overall train-validation-test split ratio is 70:24:6. No data augmentation is applied as the data size and variation are already sufficient.

### 3. Model Pipeline
The input layer is designed to receive coloured images with a dimension of 160x160. The full shape will be (160,160,3).

Transfer learning is applied for building the deep learning model of this project. Firstly, a preprocessing layer is created that will change the pixel values of input images to a range of -1 to 1. This layer serves as the feature scaler and it is also a requirement for the transfer learning model to output the correct signals.

For feature extractor, a pretrained model of MobileNet v2 is used. The model is readily available within TensorFlow Keras package, with ImageNet pretrained parameters. It is also frozen hence will not update during model training.

A global average pooling and dense layer are used as the classifier to output softmax signals. The softmax signals are used to identify the predicted class.

The model is trained with a batch size of 16 and 50 epochs. After training, the model reaches:
- 99% training accuracy and 
- 99% validation accuracy. 

## Results
The model is evaluated with the test data. The loss and accuracy are shown in figure below.

![image](https://user-images.githubusercontent.com/100325884/166852438-cd06b026-fa4d-4587-8009-377584a01c0c.png)

Some predictions are also been made with the model, and compared with the actual results.



