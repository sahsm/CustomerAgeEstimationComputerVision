# Customer Age Estimation Using Computer Vision

## Project Overview

This project develops a **computer vision and deep learning model** to estimate a person's age from facial images.

The business objective is to support age-related customer verification in a retail environment, including compliance with restrictions on the sale of age-restricted products.

The project uses **transfer learning with a pretrained ResNet50 convolutional neural network** and evaluates model performance using Mean Absolute Error (MAE).

---

## Business Problem

Retail businesses that sell age-restricted products need reliable methods to support age verification.

The objective of this project was to investigate whether computer vision could be used to estimate customer age from facial images and potentially assist employees with age-related verification decisions.

The required model performance was:

**Validation MAE < 8 years**

---

## Dataset

The dataset contains **7,591 facial images** and a CSV file containing:

- `file_name` — image filename
- `real_age` — actual age of the person in the image

The images cover a wide range of ages and include variations in facial appearance, lighting, pose, and image quality.

The image dataset is not included in this repository.

---

## Exploratory Data Analysis

The analysis included:

- Examination of the age distribution
- Statistical summary of the target variable
- Visual inspection of sample facial images
- Evaluation of the representation of different age groups

The dataset contains more observations among younger and middle-aged individuals, while older age groups are less represented.

This imbalance is important because differences in age-group representation can affect model performance across different portions of the population.

---

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

---

## Results

The training dataset contained **5,694 images**, while the validation dataset contained **1,897 images**.

The project target was:

**Validation MAE < 8 years**

The model achieved a best validation MAE of approximately:

**5.93 years**

This means that the predicted age differed from the actual age by approximately **6 years on average**.

The final model therefore exceeded the required performance target by approximately **2.07 MAE points**.

---

## Business Considerations

The model successfully exceeded the required performance target and demonstrates that transfer learning can be effectively applied to age estimation from facial images.

However, an average error of approximately 6 years is significant when the system is used for age-sensitive decisions.

For customers close to legal age thresholds, the model should therefore be used as a **decision-support tool rather than as a replacement for manual identification checks**.

The uneven representation of different age groups should also be considered before using the model in a real-world environment.

---

## What I Learned

This project strengthened my understanding of:

- Building deep learning models for image regression problems
- Applying transfer learning using pretrained convolutional neural networks
- Working with ResNet50 and ImageNet pretrained weights
- Preparing and augmenting image data for neural network training
- Adapting a pretrained classification architecture for a regression task
- Training and evaluating deep learning models with TensorFlow and Keras
- Using MAE to evaluate continuous age predictions
- Training neural networks using GPU acceleration
- Connecting model performance with real-world business limitations and risks

---

## Limitations and Future Improvements

Potential improvements include:

- Investigating model performance separately across different age groups
- Addressing the lower representation of older individuals in the dataset
- Testing additional image augmentation techniques
- Experimenting with alternative pretrained architectures
- Performing additional hyperparameter tuning
- Analyzing prediction errors to identify age ranges or image characteristics where the model performs poorly
- Evaluating the model on additional external image data before considering real-world deployment

---

## Technologies Used

- Python
- Pandas
- Matplotlib
- TensorFlow
- Keras
- ResNet50
- Computer Vision
- Deep Learning
- Transfer Learning
- Jupyter Notebook

---

## Reproducibility

The original image dataset is not included in this repository due to its size and source restrictions.

The notebook preserves the outputs from the original execution, including exploratory analysis, image samples, and GPU training results.

To reproduce the training:

1. Clone this repository.

2. Install the required dependencies:

```bash
pip install -r requirements.txt
```

3. Place the image dataset in the expected directory structure.

4. Update the dataset path in the notebook if necessary.

5. Open and run:

```text
Customer_Age_Estimation_Computer_Vision.ipynb
```

GPU acceleration is recommended for model training.

---

## Repository Structure

```text
Customer-Age-Estimation-Computer-Vision/
├── Customer_Age_Estimation_Computer_Vision.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Conclusion

A **ResNet50-based computer vision model** was successfully trained to estimate age from facial images.

The final model achieved a **validation MAE of approximately 5.93 years**, outperforming the required MAE threshold of 8 years.

The project demonstrates the practical application of transfer learning, image preprocessing, data augmentation, GPU-based deep learning training, and regression with image data while also highlighting the importance of considering model error and limitations in age-sensitive business decisions.

---

## Author

**Sara Menger**

Data Scientist  
Python • SQL • Machine Learning • Data Analytics
 
LinkedIn: https://linkedin.com/in/saramenger
