# Customer Age Estimation Using Computer Vision

## Project Overview

This project develops a computer vision model to estimate a person's age from facial images.

The business objective is to support age-related customer verification in a retail environment, including compliance with restrictions on the sale of age-restricted products.

The project uses transfer learning with a pretrained ResNet50 convolutional neural network and evaluates model performance using Mean Absolute Error (MAE).

## Dataset

The dataset contains **7,591 facial images** and a CSV file containing:

- `file_name` — image filename
- `real_age` — actual age of the person in the image

The images cover a wide range of ages and include variations in facial appearance, lighting, pose, and image quality.

The image dataset is not included in this repository.

## Exploratory Data Analysis

The analysis included:

- Examination of the age distribution
- Statistical summary of the target variable
- Visual inspection of sample facial images
- Evaluation of the representation of different age groups

The dataset contains more observations among younger and middle-aged individuals, while older age groups are less represented.

## Model

The model was built using **transfer learning with ResNet50 pretrained on ImageNet**.

The original classification head was removed and replaced with:

- Global Average Pooling
- A single output neuron for age prediction

### Image Processing

Images were:

- Resized to 150 × 150 pixels
- Normalized to the [0, 1] range
- Augmented using horizontal flipping during training

### Training Configuration

- Architecture: ResNet50
- Pretrained weights: ImageNet
- Optimizer: Adam
- Learning rate: 0.0001
- Loss function: Mean Squared Error (MSE)
- Evaluation metric: Mean Absolute Error (MAE)
- Epochs: 20
- Batch size: 16

The model was trained using GPU acceleration.

## Results

The training dataset contained **5,694 images**, while the validation dataset contained **1,897 images**.

The project target was:

**Validation MAE < 8 years**

The model achieved a best validation MAE of approximately:

**5.93 years**

This means that the predicted age differed from the actual age by approximately 6 years on average.

## Business Considerations

The model successfully exceeded the required performance target and demonstrates that transfer learning can be effectively applied to age estimation from facial images.

However, an average error of approximately 6 years is significant when the system is used for age-sensitive decisions.

For customers close to legal age thresholds, the model should therefore be used as a decision-support tool rather than as a replacement for manual identification checks.

## Technologies

- Python
- Pandas
- Matplotlib
- TensorFlow
- Keras
- ResNet50
- Computer Vision
- Deep Learning
- Transfer Learning

## Reproducibility

The original image dataset is not included in this repository due to its size and source restrictions.

The notebook preserves the outputs from the original execution, including exploratory analysis, image samples, and GPU training results.

To reproduce the training, place the dataset in the expected directory structure and update the dataset path if necessary. Required Python dependencies are listed in `requirements.txt`.

## Repository Structure

```text
Customer-Age-Estimation-Computer-Vision/
├── Customer_Age_Estimation_Computer_Vision.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

Conclusion

A ResNet50-based computer vision model was successfully trained to estimate age from facial images.

The final model achieved a validation MAE of approximately 5.93 years, outperforming the required MAE threshold of 8 years.

The project demonstrates the use of transfer learning, image preprocessing, data augmentation, GPU-based deep learning training, and regression with image data.