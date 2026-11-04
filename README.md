# Efficient Image Clustering Using SIFT + CNN Ensemble Features

**A Comparative Study of Handcrafted Features, Deep Learning Features, and Feature Fusion for Unsupervised Image Clustering**

## Project Overview

This project explores unsupervised image clustering by combining traditional computer vision techniques with deep learning feature extraction.

It investigates whether combining **SIFT (Scale-Invariant Feature Transform)** descriptors with **MobileNetV2 CNN features** can improve image clustering performance compared with using either feature representation independently.

The experiments are conducted using a selected subset of the **Caltech-101 dataset**, containing 604 images from 10 object categories.

## Objectives

- Extract local image features using SIFT.
- Construct a Bag of Visual Words (BoVW) representation.
- Apply Principal Component Analysis (PCA) for dimensionality reduction.
- Extract deep visual features using pretrained MobileNetV2.
- Investigate different feature-fusion strategies.
- Perform unsupervised clustering using K-Means.
- Evaluate clustering performance using Silhouette Score, Adjusted Rand Index (ARI), and Normalized Mutual Information (NMI).

## Dataset

The project uses a subset of the Caltech-101 dataset.

**Selected categories:**

1. Dolphin
2. Minaret
3. Trilobite
4. Lamp
5. Water Lily
6. Panda
7. Wheelchair
8. Buddha
9. Crocodile
10. Ceiling Fan

**Dataset statistics:**

| Description | Value |
|---|---:|
| Selected categories | 10 |
| Total images | 604 |
| SIFT descriptors | 257,847 |
| BoVW vocabulary size | 200 |
| SIFT reduced dimensions | 50 |
| MobileNetV2 feature dimensions | 1,280 |
| Final fusion dimensions | 50 |
| Number of clusters | 10 |

## Methodology

### 1. SIFT Feature Extraction

SIFT identifies local keypoints and extracts 128-dimensional descriptors from images.

### 2. Bag of Visual Words (BoVW)

MiniBatch K-Means is used to create a visual vocabulary of 200 visual words. Each image is represented using a 200-dimensional histogram.

### 3. Dimensionality Reduction

PCA reduces the SIFT feature representation from 200 dimensions to 50 dimensions.

### 4. CNN Feature Extraction

MobileNetV2, pretrained on ImageNet, is used as a deep feature extractor.

Each image produces a 1,280-dimensional feature vector, which is subsequently reduced to 50 dimensions using PCA.

### 5. Feature Fusion

The project investigates six fusion strategies:

- Averaging Fusion
- Weighted Fusion
- Power/Gamma Fusion
- Logarithmic Fusion
- Exponential Fusion
- Geometric Mean Fusion

### 6. Image Clustering

K-Means clustering is applied with 10 clusters.

### 7. Evaluation

The following metrics are used:

- **Silhouette Score:** Evaluates cluster separation and cohesion.
- **Adjusted Rand Index (ARI):** Measures agreement between predicted clusters and actual category labels.
- **Normalized Mutual Information (NMI):** Measures the information shared between cluster assignments and actual labels.

## Experimental Results

The following results are reproduced from the project presentation.

| Method | Silhouette | ARI | NMI |
|---|---:|---:|---:|
| SIFT (BoVW + PCA) | -0.0122 | 0.0378 | 0.0946 |
| MobileNetV2 | 0.0756 | 0.7827 | 0.8941 |
| Averaging Fusion | 0.1911 | 0.8801 | 0.9401 |
| Weighted Fusion | 0.1702 | 0.9100 | 0.9513 |
| Power/Gamma Fusion | 0.1205 | 0.8640 | 0.9261 |
| Log Fusion | 0.1552 | 0.7712 | 0.8880 |
| Exponential Fusion | 0.8377 | 0.0012 | 0.0307 |
| Geometric Mean Fusion | 0.0246 | 0.2957 | 0.5746 |

**Main observation:** MobileNetV2 features perform substantially better than SIFT features alone. The presentation reports that weighted fusion achieves the highest ARI and NMI among the evaluated methods.

*Note: The fusion method labels should be verified against a clean notebook execution because the saved notebook output order appears inconsistent with the presentation labels.*

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| OpenCV | SIFT feature extraction |
| NumPy | Numerical computations |
| Scikit-learn | PCA, K-Means and evaluation |
| TensorFlow / Keras | MobileNetV2 feature extraction |
| Matplotlib | Data visualisation |
| PIL | Image processing |
| Google Colab | Development and execution |
| Google Drive | Dataset storage |

## Project Structure

```text
Efficient-Image-Clustering/
│
├── README.md
│
├── notebooks/
│   └── Cv_Project_Final.ipynb
│
├── presentation/
│   └── CV_Project_Presentation.pdf
│
├── reports/
│   └── Efficient_Image_Clustering_Project_Report.pdf
│
├── dataset/
│   └── Caltech101_subset/
│
└── results/
    ├── visualizations/
    ├── clustering_results/
    └── evaluation_metrics/
```

*The structure above is a suggested GitHub repository layout. Adjust the filenames and folders to match the files you actually upload.*

## How to Run

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd Efficient-Image-Clustering
```

### 2. Install dependencies

```bash
pip install numpy pandas matplotlib
pip install opencv-python scikit-learn
pip install tensorflow pillow
```

### 3. Open the notebook

Upload or open the notebook in Google Colab:

```text
notebooks/Cv_Project_Final.ipynb
```

### 4. Prepare the dataset

Download the Caltech-101 dataset and configure the dataset path in the notebook.

### 5. Execute the notebook

Run the notebook cells sequentially to perform feature extraction, dimensionality reduction, feature fusion, clustering and evaluation.

## Future Improvements

- Experiment with Spectral Clustering.
- Explore Agglomerative Clustering and DBSCAN.
- Investigate UMAP and t-SNE visualisations.
- Improve feature-fusion techniques.
- Test on larger image datasets.
- Measure computational time and memory usage.
- Investigate more advanced deep learning architectures.

## Author

**Zakariya Yahya Ally**

Data Science and Artificial Intelligence (DSAI)  
IIT Madras Zanzibar

## Academic Project

This project demonstrates the application of computer vision, unsupervised machine learning, deep feature extraction and feature engineering to image clustering.

---

**Keywords:** Computer Vision, Image Clustering, SIFT, CNN, MobileNetV2, Bag of Visual Words, PCA, Feature Fusion, K-Means, Caltech-101, Unsupervised Learning.
