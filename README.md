# Maths-Problem-Solving-Using-Image-Processing

# Project Overview

## Project name


## Project Scope

The objective of this project is to develop a computer vision algorithm along with solution package for recognizing, digitizing and validating a mathematical equation written by freehand on a paper.
The following are the modules the project has been divided into to achieve the end objective

1.	Workspace Detection module - responsible for detecting multiple workspaces in a given sheet of paper using pre-defined markers.
2.	Analysis Module - Analysis module is responsible for detecting and localizing characters in any given single workspace, and mathematically analyzing them and drawing red, green lines depending upon their correctness where green represents correct and red represents wrong answers.

## Technical Scope
This section gives a detailed description about the data set used for analytics and the various models and techniques used.

### Datasets
Two open source datasets such as MNIST and Kaggle’s mathematical symbols are used for optical character recognition.

•	MNIST - Samples provided from MNIST (Modified National Institute of Standards and Technology) dataset includes handwritten digits total of 70,000 images consisting of 60,000 examples in training set and 10,000 examples in testing set.

•	Kaggle’s Handwritten Mathematical symbols - This datasets include 82 symbols but only a few symbols such as “+”, “-”, “*”, “(”, “)” are selected. Each symbol contains at most 4000 examples Images has to be processed in the same way as MNIST before training.

### Training and Validation Split 
The dataset is split into training and validation subsets in the ratio of 8:2 using tensorflow’s image data generator.

## Workspace Detection Module
Steps involved in workspace detection

•	Finding closed rectangular boxes

•	Sorting the boxes (Top-to-Bottom) based on the coordinates

•	Choosing the desired boxes based on the area.

## Analysis Module 
Line Detection - The approach for line detection assumes that there is a sufficient gap between lines and there is some intersection between exponential characters and line. The binary images of the detected workspaces are compressed in a single array to take forward derivative thereby detecting the coordinates of each line.

Line Detection using OCRopus  - OCRopus is a collection of document analysis programs, it performs the following steps  : 

•	Binarization - Steps involved in binarization are estimating skew angle, estimating thresholds and rescaling

•	Page-Layout Analysis - Performs text line finding, this identifies the tops and bottoms of text lines by computing gradients and performs some adaptive thresholding, those components are then used as seeds for the text-line recognition.

•	Text-Line Recognition - Text line Recognition uses CLSTM. CLSTM is an implementation of the LSTM recurrent neural network model in C++, using Eigen library for numerical computations. After text line recognition each lines in the image are then extracted and saved as separate images with labels in ‘.txt’ format.

•	OCR

## Data preparation for DCCNN: 

Image pre-processing is performed prior to prediction for the extracted characters from scanned worksheet to match the training dataset.

### Training: 

•	Activation Function Softmax is used in the final layer, all other layers contain ReLu activation function 

•	Optimizers:
 
    o AdaDelta optimizer is an adaptive learning rate method which requires no manual tuning of a learning rate performed well compared to other optimizers. The parameters used are,  
       Learning Rate = 1.0  and Rho = 0.95 (decay factor)

•	Batch Normalization is used to overcome vanishing gradient problem

•	Dropout of 50 % is used before the final dense layer

•	Model is trained for only 10 epochs with accuracy up to 96 %

•	Augmentation only slightly improved accuracy in this case (Random rotations, width shift, height shift) 

## Tesseract 
Tesseract 4 adds a new neural net (LSTM) based OCR engine which is focused on line recognition. It also has a unique configuration option for detecting equation region in the document

## Flask
Flask is a lightweight WSGI web application framework, designed to make getting started quick and easy, with the ability to scale up to complex applications. 

## Handling FILE UPLOADS with flask

* Create a basic form that accepts the images to process and evaluate the sum.
  Here is a simple HTML page with a form that accepts a file:

    o <!doctype html>
        <html>
        <head>
            <title>File Upload</title>
        </head>
        <body>
            <h1>File Upload</h1>
            <form method="POST" action="" enctype="multipart/form-data">
            <p><input type="file" name="file"></p>
            <p><input type="submit" value="Submit"></p>
            </form>
        </body>
       </html>

# To evaluate and test
Clone the repository and start the flask app to use product


