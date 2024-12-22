# Malaria Identification Model

## Problem Statement

This is a problem I was tasked at addressing as part of my ADSP Capstone project. This project was worth 60% of my final mark, and the objective of this problem is as follows:

"Build an efficient computer vision model to detect malaria. The model should identify whether an image of a red blood cell is one infected with malaria or not."
## Background

Malaria is a contagious disease caused by Plasmodium parasites that are transmitted to humans through the bites of infected female Anopheles mosquitoes. The parasites enter the blood and begin damaging red blood cells (RBCs) that carry oxygen, which can result in respiratory distress and other complications. The lethal parasites can stay alive for more than a year in a person’s body without showing any symptoms. Therefore, late treatment can cause complications and could even be fatal.

Traditional diagnosis of malaria in the laboratory requires careful inspection by an experienced professional to discriminate between healthy and infected red blood cells. It is a tedious, time-consuming process, and the diagnostic accuracy (which heavily depends on human expertise) can be adversely impacted by inter-observer variability. An automated system can help with the early and accurate detection of malaria.

Applications of automated classification techniques using Machine Learning (ML) and Artificial Intelligence (AI) have consistently shown higher accuracy than manual classification. It would therefore be highly beneficial to propose a method that performs malaria detection using Deep Learning Algorithms.
## Goal

The goal is to create an efficient deep learning model that takes in an image of a red blood cell, and accurately predicts whether this cell is 'infected' or 'uninfected'. To do this, we will be developing two CNN models and test their performance, identifying which model performs best and (ideally) implement this in the healthcare system. 

The effectiveness of this model will determine how reliably malaraia detection can be moved to a computer-based deduction system versus doing it visually using manual labor. 

## Image Processing

The dataset provided has images of red blood cells in RGB, where we are given 24958 images for training, and 2600 images for testing. Of the images in the training set, 12376 images are 'uninfected' and 12582 images are 'infected'. Of the images in the testing set, there are 1300 'uninfected' and 'infected' images. 

To investigate which model performs better, we will also be modifying the original images slightly to determine whether RGB is the optimal way to present the images to a computer. To this end, all images in the dataset are further converted into HSV, presenting the same image in a slightly different way.

| RGB | HSV |
| --- | --- |
|     |     |

## Model Building

Two models are developed to investigate the effectiveness of a computer vision model for malaria detection. 

- The first model (Model 1) is a simple model, that has fewer layers and does not involve normalization between the layers.
- The second model (Model 2) is more complex, with additional layers, normalization between layers and the implementation of the `leakyrelu` activation function to avoid the dying activation function problem we may face.

The models can be found under the "Model Building" section of the "Deep_Learning_Malaria_Detection.ipynb" notebook. 

Each model is tested with the original RGB images, and then the HSV images to determine whether a difference in the source data makes a tangible difference in the results. 

## Results

### Using Model 1

Model 1 is designed to be a basic model that gives some insight into how the problem can be approached. It features 4 layers, with only two hidden layers. The `relu` activation function is used and the model is tested on the RGB images, and the HSV images. 

The model trained on the HSV images outperforms the model trained on the RGB images, suggesting that HSV images are easier to analyze and identify the current state of the cell with more clarity. Only 0.8% of cases were identified as a false negative (the deadliest case) which falls within an acceptable margin. 
### Model 2

Model 2 is designed to build on Model 1. It features more layers (5 layers in this model), and normalization between the layers to speed up the learning process, and aid in the generalization of study. Theoretically, this would outperform the first model implemented at the cost of a longer training time. 

However, this does not seem to be the case. In both the RGB and HSV implementations, the model seems to overfit on the data, suggesting that the model may be too complex to generalize the patterns effectively. It performs poorer than Model 1 (HSV) in terms of recall, as higher recall implies the fewer false negatives reported.
## Results & Recommendations

Model 1 tested with HSV images yields a 99% Recall, making it the best model in the context of the problem. We want to accurately predict the infected cells as often as possible, and so having a high recall is of the utmost importance. It does not take too long to train the model, and can be done efficiently with minimal costs using Google Colab's cloud computing spaces and leveraging their GPUs. 

From a business perspective, it would be highly beneficial to implement such a compter vision model in the healthcare industry. The model can identify the state of the cell much faster than done manually, and eliminates the risk of inter-observer variability. The benefits would outweigh any costs involved as the business would save money on running expensive technology and manpower analyzing bloods to arrive at the same result.
## Risks 

The risks, while minimal, could potentially be deadly when the model predicts a false negative. Further analysis is encouraged after the implementation of this model if possible, to ensure 100% certainty in the result's truth.