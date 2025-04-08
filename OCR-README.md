# Egyptian National ID Classification

This project focuses on the classification of categorical fields in the Egyptian National ID. The fields include **gender**, **religion**, and **marital status**. The data consists of segmented images for each field, and a Convolutional Neural Network (CNN) is used to classify each field.

## Project Overview

The goal of this project is to extract information from the Egyptian National ID through segmentation of images. Specifically, this project classifies:
- **Gender** (Male/Female)
- **Religion** (Muslim/Christian)
- **Marital Status** (Single/Widowed/Married)

Each field is classified using separate models due to differences in class distribution and balance in each field. The model architecture is a simple CNN, which has shown good results for this classification task.

## Key Steps

1. **Data Preprocessing:**
   - **Data Loading:** The segmented images for each field are loaded and preprocessed.
   - **Image Resizing:** Each image is resized and converted to numpy arrays suitable for training.
   - **Train-Test Split:** Data is split into training, validation, and test sets using a stratified split.

2. **Model Architecture:**
   - **Gender Classification (Male/Female):**
     - **Output Layer:** Sigmoid activation for binary classification.
     - **Challenge:** This is the simplest of the tasks as it’s a binary classification.
       
   - **Religion Classification (Muslim/Christian):**
     - Added Batch normlization and dropout to reduce overfitting.
     - **Output Layer:** Softmax activation for binary classification.
     - **Challenge:** Class imbalance (Christian was the minority class). Also, labels are represented differently for males and females in Arabic.
       
   - **Marital Status Classification (Single/Widowed/Married):**
     - Added Batch normlization and dropout and l2 reularization to reduce overfitting.
     - **Output Layer:** Softmax activation for multi-class classification.
     - **Challenge:** Class imbalance (Widowed had only one sample), with different representations for gender-based labels in Arabic.
       
 3. Challenges
    - **Class Imbalance:** The minority classes (Christian and Widowed) were augmented with synthetic data to improve model performance.
    - **Gender-based Labeling in Arabic:** Some fields had different label representations for males and females, which were handled during preprocessing.

4. **Handling Class Imbalance:**
   - **Data Synthesis and Augmentation:** For classes with few samples (e.g., Christian and Widowed), synthetic data was generated to balance the dataset.
   - **Gender-based Representation:** The labels were carefully handled to ensure correct representation for male and female categories in Arabic.

5. **Training and Evaluation:**
   - A simple CNN was used for each classification task.
   - Results were evaluated based on accuracy, F1 score (to account for class imbalance), and other performance metrics.

## Results
- **Gender:**
    - **F1 Score (Test):** 98.9%

- **Religion:**
    - **F1 Score (Test):** 99.5%

- **Marital Status:**
    - **F1 Score (Test):** 99.4%


## Usage

Since the data used in this project is confidential and cannot be shared, you will need your own dataset in the same format to replicate or continue the project. The general steps and methodology can be followed to apply the models to similar segmented image data.

