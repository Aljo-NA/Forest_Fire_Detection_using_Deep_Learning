# Forest Fire Detection Using Deep Learning

## Overview

This project uses a Convolutional Neural Network (CNN) to classify
images into two classes:

-   **Fire**
-   **No Fire**

The project was developed in Google Colab using Python and
TensorFlow/Keras. The workflow includes image dataset preparation, data
cleaning, preprocessing, CNN training, model evaluation, and prediction
on new images.

## Project Workflow

1.  Upload and extract the Forest Fire dataset.
2.  Check the dataset structure.
3.  Load training and testing images.
4.  Check for duplicate images.
5.  Check for corrupted images.
6.  Analyze the class distribution.
7.  Resize images to **64 × 64** pixels.
8.  Convert images to **grayscale**.
9.  Normalize image values.
10. Apply image augmentation to the training data.
11. Train a CNN model.
12. Evaluate the model using test accuracy and a classification report.
13. Generate predictions for new images.
14. Send an email alert when a fire is detected.

## Dataset

The notebook uses a directory-based image dataset with two classes:

``` text
Forest Fire Dataset/
├── Training/
│   ├── fire/
│   └── nofire/
└── Testing/
    ├── fire/
    └── nofire/
```

The notebook initially loaded:

-   **Training images:** 1,520
-   **Testing images:** 379
-   **Training classes:** 760 Fire and 760 No Fire
-   **Testing classes:** 189 Fire and 190 No Fire

The dataset was checked for duplicate and corrupted images, and none
were removed during the recorded run.

## Data Preprocessing

The project performs several preprocessing steps:

-   Images are resized to **64 × 64** pixels.
-   Images are converted to **grayscale**.
-   Pixel values are scaled using `1./255` during model input
    preparation.
-   Training data uses image augmentation, including:
    -   Rotation
    -   Width and height shifting
    -   Shearing
    -   Zooming
    -   Horizontal flipping

These steps help prepare the images for CNN training and provide
variation in the training data.

## CNN Architecture

The model is implemented using TensorFlow/Keras.

``` text
Input: 64 × 64 × 1 grayscale image
        ↓
Conv2D - 32 filters, 3 × 3, ReLU
        ↓
MaxPooling2D
        ↓
Conv2D - 64 filters, 3 × 3, ReLU
        ↓
MaxPooling2D
        ↓
Flatten
        ↓
Dense - 128 units, ReLU
        ↓
Dense - 1 unit, Sigmoid
        ↓
Fire / No Fire
```

### Training Configuration

-   Optimizer: **Adam**
-   Loss function: **Binary Cross-Entropy**
-   Metric: **Accuracy**
-   Batch size: **32**
-   Epochs: **15**
-   Input color mode: **Grayscale**

## Model Performance

On the recorded test evaluation:

-   **Test Accuracy: 91.82%**
-   Test samples: **379**

The recorded classification report shows approximately:

  Class                Precision   Recall   F1-Score
  ------------------ ----------- -------- ----------
  Fire                      0.92     0.92       0.92
  No Fire                   0.92     0.92       0.92
  Overall Accuracy                              0.92

A confusion matrix is also generated to examine the classification
results.

## Prediction

The trained model can be loaded and used to classify a new uploaded
image.

The notebook:

1.  Loads the trained CNN model.
2.  Accepts an image upload.
3.  Resizes the image to 64 × 64.
4.  Converts it to grayscale.
5.  Normalizes the image.
6.  Generates a prediction.
7.  Displays whether fire is detected.

The recorded example produced:

``` text
Prediction Score: 0.1947
Result: Fire Detected
```

## Alert System

The notebook also contains an email-alert component using Python's SMTP
functionality. When the prediction indicates fire, an email notification
can be sent.

**Security note:** Email credentials or app passwords should never be
stored directly in source code or committed to GitHub. Use environment
variables or another secure secrets-management method before publishing
this project.

## Technologies Used

-   Python
-   TensorFlow
-   Keras
-   Deep Learning
-   Convolutional Neural Network (CNN)
-   NumPy
-   Pandas
-   Scikit-learn
-   Pillow
-   Matplotlib
-   Google Colab
-   SMTP / Python Email Libraries

## Project Structure

``` text
Forest-fire-detection/
├── Forest_fire_detection_Using_deep_learning.ipynb
├── README.md
└── forest_fire_cnn_model_gray.h5   # optional; do not upload if repository-size limits apply
```

## How to Run

### Google Colab

1.  Open the `.ipynb` notebook in Google Colab.
2.  Upload the Forest Fire dataset ZIP file when prompted.
3.  Run the notebook cells in order.
4.  Train the CNN model.
5.  Evaluate the model.
6.  Upload a new image in the prediction section to test the model.

## Applications

This project demonstrates how deep learning and computer vision can be
used for image-based forest fire detection and automated alerting.

## Future Improvements

Possible improvements include:

-   Using transfer learning with a pretrained CNN model.
-   Increasing and diversifying the dataset.
-   Evaluating additional metrics and error cases.
-   Building a web interface for real-time image prediction.
-   Integrating a camera/video stream for continuous detection.
-   Moving email credentials to secure environment variables.

## Author

**Aljo N A**

B.Tech -- Artificial Intelligence & Data Science\
Jyothi Engineering College
