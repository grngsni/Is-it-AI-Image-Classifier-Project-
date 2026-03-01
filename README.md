# Is it AI?

## Introduction
As a personal project, I created a simple image classifier to distinguish between an AI-generated and human image using [fastai](https://docs.fast.ai/) - a deep learning library built atop PyTorch.  

## Problem Statement
With the advancement of generative AI, distinguishing between authentic and AI-generated visual content has become increasingly challenging. Synthetic images are being leveraged for scams, identity theft, and large-scale misinformation campaigns. To address this issue, this project builds a Convolutional Neural Network to classify a given image as either AI-generated or a real human photograph.

## About the Dataset
To procure the data, I used the [ddgs](https://pypi.org/project/ddgs/) Python library for a small sample size of 200 images to train the model, 80% of which was used for training and the rest for validation. 

## Methodology
I used the **resnet18** CNN classifier to train the model using the following procedure:  
1. **Data Preparation:** Collected a total of 200 images that included both AI-generated and human images.  
2. **Training the model:** Created a `DataBlock` (similar to `DataLoaders` in PyTorch) and trained the resnet18 model using it.  
3. **Cleaning the model:** Using the `plot_top_losses` function I visualized the loss values the model produces. Based on the highest loss value the `ImageClassifierCleaner` function is used to manually re-classify the incorrect classifications. In this specific case, I was able to identify 6 misclassifications of AI-generated images as human images and correct them.
4. **Using the model:** Tested the model with the image of a human which it correctly classified.  
5. **Evaluation:** The model is evaluated using the confusion matrix. 

## Result 
Before data cleaning, the model performed accordingly:
| Metric | Value |
| ----------- | ----------- |
| Accuracy | 82% |
| Precision | 100% |
| Recall | 64% |
| F1 Score | 78% |  

After cleaning, the model achieved perfect scores in all evaluation metrics.
