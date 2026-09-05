# Facial Emotion Recognition Using CNN & VGG16

A deep learning project for **facial emotion recognition** using the **FER-2013 dataset**. The project explores two different approaches for classifying facial expressions into seven emotion categories:

* **Custom Convolutional Neural Network (CNN)**
* **VGG16 Transfer Learning**

The models take facial images as input and predict the emotion expressed in the face.

---

## Project Overview

Facial Emotion Recognition is a computer vision classification problem where a model learns to identify human emotions from facial expressions.

This project uses grayscale facial images and classifies them into **7 emotion categories**:

| Label | Emotion  |
| ----: | -------- |
|     0 | Angry    |
|     1 | Disgust  |
|     2 | Fear     |
|     3 | Happy    |
|     4 | Sad      |
|     5 | Surprise |
|     6 | Neutral  |

The original FER-2013 images are **48 × 48 grayscale facial images**.

---

## Dataset

The project uses the **FER-2013 (Facial Expression Recognition 2013)** dataset.

The dataset contains:

* **28,709 training images**
* **3,589 public test samples**
* **3,589 private test samples**
* Image size: **48 × 48**
* Image type: **Grayscale**
* Number of classes: **7**

Each image is categorized according to the emotion expressed by the person.

---

## Project Workflow

The project follows the following pipeline:

```text
FER-2013 Dataset
       ↓
Image Loading
       ↓
Image Resizing & Preprocessing
       ↓
Exploratory Data Analysis
       ↓
Train / Validation Split
       ↓
Data Augmentation
       ↓
      ┌─────────────────────┐
      │                     │
      ↓                     ↓
Custom CNN             VGG16 Transfer
                          Learning
      │                     │
      └──────────┬──────────┘
                 ↓
             Evaluation
                 ↓
      Model Comparison
                 ↓
        Real Image Testing
```

---

## Exploratory Data Analysis

Before training, the dataset was explored to understand the distribution of the different emotion classes.

The project visualizes the number of images belonging to each emotion and investigates the class distribution of the training data.

---

## Data Preprocessing

The images are:

* Resized to **48 × 48 pixels**
* Converted to grayscale for the custom CNN
* Converted to the required input format for VGG16
* Split into training and validation sets
* Normalized before training

The training data is also augmented to help the models generalize better to unseen facial images.

### Data Augmentation

Image augmentation is used to generate variations of training images and reduce overfitting.

The augmentation pipeline is used during model training rather than manually creating additional image files.

---

# Model 1 — Custom CNN

The first approach uses a CNN architecture designed specifically for the emotion-recognition task.

The network contains multiple convolutional blocks with:

* Convolutional layers
* ReLU activation
* Batch Normalization
* Max Pooling
* Dropout
* Fully connected layers
* Softmax output layer

The final layer contains **7 neurons**, corresponding to the seven emotion classes.

### Training

The model is trained using:

* **Adam Optimizer**
* **Categorical Cross-Entropy Loss**
* Up to **60 epochs**
* Early Stopping

The training and validation performance are monitored using loss and accuracy curves.

---

# Model 2 — VGG16 Transfer Learning

The second approach uses **VGG16**, a pretrained convolutional neural network originally trained on ImageNet.

The pretrained VGG16 convolutional base is used as a feature extractor, followed by custom fully connected layers:

```text
Input Image
     ↓
VGG16 Convolutional Base
     ↓
Flatten
     ↓
Dense (512)
     ↓
Batch Normalization
     ↓
Dropout
     ↓
Dense (256)
     ↓
Batch Normalization
     ↓
Dropout
     ↓
Dense (7)
     ↓
Softmax
```

The model is trained using:

* **Adam Optimizer**
* Learning rate: `1e-4`
* **Categorical Cross-Entropy**
* Up to **50 epochs**
* Early Stopping
* Learning Rate Reduction

---

## Evaluation

Both models are evaluated on the test dataset using several methods.

### Accuracy & Loss

Training and validation curves are plotted to analyze:

* Training loss
* Validation loss
* Training accuracy
* Validation accuracy

These plots help identify potential overfitting and understand the training behavior of each model.

### Classification Report

A classification report is generated containing:

* Precision
* Recall
* F1-score
* Support

for each emotion category.

### Confusion Matrix

A confusion matrix is used to analyze which emotions are correctly classified and which emotions are commonly confused with each other.

---

## Model Comparison

The project compares the predictions of the:

**Custom CNN vs. VGG16**

The comparison includes predictions on the same test images and examines how both models perform relative to the actual emotion labels.

Example comparison:

```text
                ┌───────────────┐
                │ Test Image    │
                └───────┬───────┘
                        │
              ┌─────────┴─────────┐
              ↓                   ↓
        Custom CNN             VGG16
              │                   │
              ↓                   ↓
        Prediction             Prediction
              └─────────┬─────────┘
                        ↓
                  Compare with
                  Ground Truth
```

---

## Real-World Testing

The project also tests both trained models on real facial images outside the original test dataset.

The predictions from the custom CNN and VGG16 model are compared to observe how well the models generalize to real-world facial expressions.

---

## Technologies Used

* **Python**
* **TensorFlow / Keras**
* **OpenCV**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **VGG16**
* **Jupyter Notebook / Google Colab / Kaggle**

---

## Project Structure

```text
Facial-Emotion-Recognition/
│
├── Facial_Emotion_Recognition.ipynb
├── README.md
└── ...
```

---

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Facial-Emotion-Recognition.git
cd Facial-Emotion-Recognition
```

### 2. Install dependencies

```bash
pip install tensorflow opencv-python numpy pandas matplotlib seaborn scikit-learn
```

### 3. Download the FER-2013 dataset

Download the dataset and organize it according to the paths used in the notebook.

### 4. Run the notebook

Open:

```text
Facial_Emotion_Recognition.ipynb
```

The notebook can be run using **Google Colab, Kaggle, or Jupyter Notebook**.

---

## Key Concepts Demonstrated

This project demonstrates practical experience with:

* Image classification
* Convolutional Neural Networks
* Transfer Learning
* VGG16
* Data Augmentation
* Batch Normalization
* Dropout
* Model training and validation
* Classification metrics
* Confusion matrices
* Model comparison
* Real-world image inference

---

## Future Improvements

Possible improvements include:

* Using more advanced architectures such as ResNet, EfficientNet, or MobileNet
* Applying class balancing techniques
* Hyperparameter tuning
* Fine-tuning the pretrained VGG16 layers
* Improving performance on minority emotion classes
* Deploying the model as a web or mobile application
* Real-time emotion recognition using a webcam

---

## Author

**Seif Elmezaien**

Computer Science Graduate | Data Science & Machine Learning

---

## License

This project is intended for educational and portfolio purposes.
