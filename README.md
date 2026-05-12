# 👤 Face Recognition using PCA & LDA

A machine learning project exploring dimensionality reduction techniques for facial recognition. This repository implements and compares Principal Component Analysis (PCA) and Linear Discriminant Analysis (LDA), classifying the extracted features using a K-Nearest Neighbors (K-NN) classifier.

> 📖 **Detailed Analysis & Code:** Please refer to the main experiments in the [notebook](faces_vs_nonfaces.ipynb).

## ✨ Key Features
- **Dimensionality Reduction:** Implementation of standard PCA and LDA from scratch.
- **Advanced Variations:** Exploration of Randomized PCA, Kernel PCA, and Shrinkage LDA for handling high-dimensional data and non-linear relationships.
- **Binary & Multi-class Classification:** Classifying distinct subjects as well as distinguishing "Faces" from "Non-Faces."
- **Hyperparameter Tuning:** Analyzing the effect of variance retention ($\alpha$), K-NN neighbors ($k$), and train/test split ratios on model accuracy.

## 🗂️ Dataset
We utilized the AT&T Face Database from Kaggle.
- **Size:** 400 images (40 distinct subjects, 10 images per subject).
- **Format:** 92x112 pixels, grayscale.
- **Splits Tested:** 50/50 and 70/30 training-to-testing ratios.

We also introduced a custom Non-Faces dataset to test the robustness of our models against random imagery (e.g., airplanes, motorbikes, etc.).

## 🧠 Methodology

1. **Principal Component Analysis (PCA)**

PCA is a dimensionality reduction technique used to extract important features from high-dimensional datasets. It works by identifying the principal components, which are linear combinations of the original features that capture the most variation in the data. We used PCA to extract these features from the face images, creating a subspace of "Eigen-Faces."

*The first two Eigen-faces:*
- ![image](https://user-images.githubusercontent.com/84376570/226113767-05d70c78-6322-46bd-9952-c6d1c7a2bf2c.png)
- ![image](https://user-images.githubusercontent.com/84376570/226113790-6725cba6-696b-4edc-9b90-b6f745411572.png)

2. **Linear Discriminant Analysis (LDA)**

Unlike PCA, which maximizes overall variance, LDA is a supervised technique that maximizes the distance between different classes while minimizing the variance within each class.

3. **Classification (K-NN)**

The projected data from both PCA and LDA was fed into a K-NN classifier, evaluated across different values of $k$ (1, 3, 5, 7) to find the optimal decision boundary.

## 📊 Key Results & Insights
- **Best Performance:** The models achieved up to 95.83% accuracy using a 70/30 data split.
- **PCA vs. Variations:** While standard PCA performed well, Kernel PCA (RBF) proved computationally expensive and sensitive to parameters, making standard/randomized PCA more practical for this linear-leaning dataset.
- **LDA Robustness:** Shrinkage LDA successfully stabilized covariance estimates, proving highly effective for our high-dimensional, small-sample-size data.
- **Faces vs. Non-Faces Challenge:** As we injected more non-face images into the testing space, the K-NN classifier's accuracy decreased. The added noise caused the spatial gaps between classes to shrink, highlighting a limitation in distance-based classification when introduced to highly complex, noisy spaces.

## 🔍 Success & Failure Cases
Sample classifications when distinguishing faces from non-faces:

- **PCA:**
+ ![image](https://user-images.githubusercontent.com/84376570/226126375-a50263e2-d5c9-40b4-9497-88e8a0387e91.png)

- **LDA:**
+ ![image](https://user-images.githubusercontent.com/84376570/226126647-0dfb68e5-6ff9-4e15-9b28-758d04d1e4cf.png)

## 🤝 Contributors

- [Ziad Mohamed](https://github.com/ziad-mohamed-7)
- [Domadios Morkos](https://github.com/DomaMorcos)
- [Karim ElNaggar](https://github.com/karimnaggar4040)
- [Ahmed Walaa](https://github.com/Ahmed-Walaaeldin)
