# Machine Learning Approaches for the Estimation of MGMT Genotype in Brain Cancer Patients <br>

# Table of Contents
1. [Introduction](#Introduction)
2. [Dataset](#Dataset)
3. [Implementation](#Implementation)
4. [Results](#Results)
5. [Future Scope](#Future-Scope)

# Introduction
A brain tumor is a growth of cells in the brain that multiplies in an uncontrolled, abnormal way. Some brain tumors are noncancerous (benign), and some are cancerous (malignant).

## Glioma 
* A glioma is a tumor that forms in the brain or spinal cord when glial cells grow out of control.
* Pituitary tumors are abnormal growths that develop in the pituitary gland.
* A meningioma tumor arises from the meninges, the membranes that surround the brain and spinal cord.

## Glioblastoma
* Glioblastoma (GBM) is an aggressive type of brain cancer, classified as Grade IV.
* It is associated with an improved response to chemotherapy with temozolomide and a patient's overall survival.

## MGMT
* MGMT promoter methylation status is a widely accepted biomarker in glioblastoma.
* Pituitary tumors are abnormal growths that develop in the pituitary gland.
* A meningioma tumor arises from the meninges, the membranes that surround the brain and spinal cord.

# Dataset

## UPENN GBM
* UPenn-GBM is a publicly available dataset of 630 patients diagnosed with de novo GBM.
* It is the largest comprehensive GBM dataset currently available.
* The dataset includes multi-parametric MRI scans, gene expression profiles, DNA methylation profiles, and clinical data.
* Clinical data includes patient demographics, treatment history, and survival outcomes.

## Patient Data
* Each patient has 4 brain MRI scans: T1-weighted, T2-weighted, T1 post-contrast, and T2-FLAIR MRI.
* Each patient has 155 slices of brain images.
* Clinical features include GLCM, Morphologic, Survival days, Age, Gender, and MGMT status.

# Implementation
## Feature Extraction

The feature extraction process is a critical step in this project, and it involves two branches, one using AlexNet and the other using VGGNet. Here's how it works:

- **AlexNet Branc**h: AlexNet is used to extract features from the input data. It processes the input features and extracts 256 relevant features. Feature selection is further performed using Recursive Feature Elimination (RFE) with a Support Vector Machine (SVM), resulting in the selection of the top 30 most informative features.

- **VGGNet Branch**: Similarly, VGGNet is used to extract features from the data. It processes the input features and extracts 512 features. These features are also subject to RFE with SVM, which selects the top 60 features with the highest significance.

- **Merged Features**: The selected features from both branches are merged together to create a combined feature set. This combined feature set consists of 90 features in total.

- **Fusion**: The features from both the AlexNet and VGGNet branches are concatenated together. This step creates a feature set that is ready for further refinement.

- **Remove Similar Features**: To ensure that the feature set is diverse and non-redundant, a process is applied to eliminate features that are highly correlated or similar. This results in a refined set of 120 distinct features.

## Training Environment

The training process involves several steps:

* **Data Preprocessing**: Before training the model, the data is preprocessed. RGB images are resized to 256x256 pixels, and pixel values are normalized to the range [0, 1] for computational efficiency.

* **Experiment Setup**: For training and evaluation, 90% of the dataset is used as training data, and the remaining 10% is designated for testing.

* **Optimizer**: Stochastic Gradient Descent (SGD) optimizer is used for training the neural network model. The initial learning rate is set at 0.001, and this rate may be adjusted during training.

* **Software Environment**: The entire implementation process takes place in a Jupyter Notebook environment.

## Training Process

The training process involves the following steps:

* **Feature Merging**: The features extracted from the AlexNet and VGGNet branches are merged, creating a comprehensive feature set.

* **Correlation Analysis**: To ensure that the feature set is not overwhelmed by highly correlated features, a correlation analysis is performed to remove similar or redundant features.

* **SVM Model Training**: The dataset is divided into training and testing sets. A Support Vector Machine (SVM) model is trained using Stratified K-fold cross-validation, ensuring a robust and reliable model.

* **Feature Scaling**: Both the training and testing data are scaled using the mean and standard deviation values calculated from the training data. This step ensures that the data is on the same scale for consistent model training and evaluation.

* **Hyperparameter Tuning**: A Grid Search Cross-Validation approach is used to find optimal hyperparameters for the SVM model. Parameters such as 'C,' 'kernel,' and 'gamma' are explored to identify the best configuration.

* **Model Evaluation**: The performance of the SVM model is evaluated using the Receiver Operating Characteristic Area Under the Curve (ROC AUC) score. Stratified K-fold cross-validation is employed to ensure that the model's performance is assessed rigorously.

The detailed steps mentioned in the "Training Process" section are crucial for creating a robust model capable of predicting the MGMT promoter methylation status accurately. The combination of feature extraction, fusion, and thorough evaluation ensures that the model's predictions are meaningful and reliable.

# Results
![Screenshot (1571)](https://github.com/gelsonm/3D-BRAIN-MRI-DETECTION/assets/37416550/9bdd8543-0cec-4900-86a7-47dba593aeb9)
![Screenshot (1569)](https://github.com/gelsonm/3D-BRAIN-MRI-DETECTION/assets/37416550/efeca190-0397-4f89-ba56-d63d7adaaf24)

![Screenshot (1574)](https://github.com/gelsonm/3D-BRAIN-MRI-DETECTION/assets/37416550/53467858-5111-4445-b47b-a23a88faf2d3)
![Screenshot (1573)](https://github.com/gelsonm/3D-BRAIN-MRI-DETECTION/assets/37416550/5dfc21b2-eb88-4108-bca1-0fb25427eea9)



# Future Scope
* Calculation of MGMT Index.
* Using MGMT Index as a new feature for further prediction of Overall Survival.
* Inclusion of other types of data (clinical or gene expression) for further experimentation.
  
