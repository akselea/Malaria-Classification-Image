# Malaria Classification Blood Sample Model

**Made by Aksel E**

## Background

Malaria is one of the life-threatening disease caused by the Plasmodium parasite and transmitted through the bite of infected mosquitoes. It affects millions of people worldwide, particularly in tropical and subtropical regions. Here show of a map where approximately malaria transmission occurs around the world.

<div align= "center">
  <img src="https://github.com/akselea/Malaria-Classification-Image/assets/116968275/da3bfd13-2ba2-4fe6-997a-03d8aba85ec1">
</div>

<div align= "center">
  Image 1. World Map that Show an Approximation where Malaria Transmission Occurs (CDC, 2020)
</div>

<br>
One of the ways to check malaria is on microscopic examination of blood smears to detect the presence of the parasite. However, this approach is time-consuming and requires skilled microscopists. With the advancements in machine learning and computer vision, automated systems for malaria detection have emerged, enabling faster and more accurate diagnosis.

Malaria Classification Blood Sample Model is a machine learning model developed to classify microscopic images of blood samples as either infected with malaria parasites or uninfected. By analyzing the unique characteristics and patterns present in the images, the model can accurately identify and classify malaria-infected cells.

This model bulit with convolutional neural networks (CNNs), one of the deep learning algorithm that used to learn and extract meaningful features from the blood sample images. Through a process of training on a large dataset of labeled images, the model can learn to differentiate between infected and uninfected cells based on visual cues, such as the appearance of parasites or abnormal cell structures.

## Data Understanding

Link into Dataset: [Malaria Blood Sample Dataset](https://www.kaggle.com/datasets/iarunava/cell-images-for-detecting-malaria)

The dataset that used in this model is a Malaria Blood Smears Sample that contained about 27560 samples, which are divided by two main folder:
- Infected Blood Samples with 13780 samples.
- Uninfected Blood Samples with 13780 samples.

Image below shown example of random sample in each folder.

<div align= "center">
  <img src="https://github.com/akselea/Malaria-Classification-Image/assets/116968275/2932b190-9012-459e-af56-c711ccce0aa0">
</div>

<div align= "center">
  Image 2. Example of Random Sample in Each Folder in Malaria Blood Sample Dataset
</div>

## Data Preparation

Blood samples from this dataset is processed by `tf.keras.preprocessing.image.ImageDataGenerator()` function. This function used to generate batches of tensor image data with real-time data augmentation to avoid model from overfitting.

Here is step-to-step how blood samples data is constructed before it's used in modeling stage:

- In `train_data` section, some image processing is arranged to improve capability of the Malaria Blood Sample Classification Model and took 90% random sample from dataset.
- In `train_generator` section, the blood samples from dataset is manipulated by `train_data` image processing and also made batch data from dataset.
- In `valid_data` section, just `rescale` image processing is arranged to equalized the size of all blood samples and just took 10% random sample from dataset.
- In `valid_generator` section, the blood samples from dataset is manipulated by `valid_data` image processing and also made batch data from dataset.

Using this `tf.keras.preprocessing.image.ImageDataGenerator()` function results two class images that used in modeling stage:

- Train image with 24804 images.
- Validation image with 2754 images.

## Modeling

Table below shown hyperparameter that used in `model.fit()` process:

Table 1. Hyperparameter Value in `model.fit()` Process

|   Hyperparameter   |                  Value                  |
|:-------------------|:----------------------------------------|
| `steps_per_epoch`  | Total Data in `train_generator` (24804) |
| `epochs`           |                    15                   |
| `batch_size`       |                    16                   |
| `validation_steps` |  Total Data in `valid_generator` (2754) |

Plot image below shown accuracy and loss value of the model.

<div align= "center">
  <img src="https://github.com/akselea/Malaria-Classification-Image/assets/116968275/f7ab7c71-db5b-459f-8187-4508e99cc46e">
</div>

<div align= "center">
  Image 3. Malaria Blood Sample Model Accuracy Plot
</div>

<br>
<br>

<div align= "center">
  <img src="https://github.com/akselea/Malaria-Classification-Image/assets/116968275/63f2ef60-4180-4087-96ee-6540bf298d3c">
</div>

<div align= "center">
  Image 4. Malaria Blood Sample Model Loss Plot
</div>
