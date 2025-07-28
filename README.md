# Palm-Print-Biometric-Authentication

This project builds a **Siamese Neural Network** for biometric authentication using palm print images. It learns to verify whether two palm images belong to the same person by comparing similarity scores.

---

##  Overview

- Uses the **THUPALMLAB** palm print dataset, containing grayscale `.bmp` images of left and right hands.
- Preprocesses images and generates **similar** and **dissimilar** image pairs.
- Trains a **Siamese CNN model** to classify image pairs based on visual similarity.
- Evaluates the model using **confusion matrix**, **accuracy**, **precision**, **recall**, and **F1 score**.
- Includes a **biometric authentication function** that verifies identity using stored palm images.
- Visualizes samples, predictions, and evaluation results using `matplotlib` and `seaborn`.

---

##  Tools & Libraries

| Tool/Library           | Purpose                                       |
|------------------------|-----------------------------------------------|
| `tensorflow`           | Building and training the Siamese network     |
| `scikit-learn`         | Evaluation metrics and data splitting         |
| `matplotlib`, `seaborn`| Visualization of samples and results          |
| `tqdm`                 | Progress bars during image loading            |
| `unrar`, `wget`        | Dataset download and extraction               |

---

##  Dataset

- **Source**: [THUPALMLAB Dataset](https://ivg.au.tsinghua.edu.cn/dataset/samples_THUPALMLAB/)
- Format: `.bmp` grayscale palm print images
- Each file is named using a structure that includes:
  - Subject ID
  - Hand side (`l` or `r`)
  - Image number

---

##  Project Pipeline

### 1. **Image Preprocessing**
- Loads images in grayscale format
- Normalizes pixel values to range [0, 1]
- Organizes by subject ID and hand side

### 2. **Pair Creation**
- **Similar pairs**: different images from the same subject and hand
- **Dissimilar pairs**: images from different subjects
- Ensures balanced dataset for binary classification

### 3. **Model Architecture**
- Siamese CNN base extracts features from each image
- Feature vectors are concatenated and passed to dense layers
- Final output: similarity score (0 = different, 1 = same)

### 4. **Model Training**
- Binary classification with `binary_crossentropy` loss
- Optimized using Adam optimizer
- Uses early stopping to avoid overfitting

### 5. **Evaluation**
- Evaluates on test set using:
  - Confusion Matrix
  - Accuracy, Precision, Recall, F1 Score
- Visualizes predictions and training history

### 6. **Biometric Authentication Demo**
- Selects a stored palm image for a user
- Compares it with a new input image
- Displays similarity score and authentication result

