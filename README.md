# Spectral Clustering on Image Pixels

## Overview
This assignment is part of my coursework at FSU , this applies spectral clustering to segment an image into clusters based on pixel similarities. The clustering is performed on the `scene2.jpg` image, which consists of 82 × 128 pixels, each having three RGB color channels. The goal is to group similar pixels together based on color proximity using an affinity-based clustering approach.

## Steps Implemented
### 1. Image Preprocessing
- Load the `scene2.jpg` image from Canvas as an 82 × 128 × 3 array.
- Normalize the pixel values by dividing by 255 to scale them between 0 and 1.

### 2. Constructing the Affinity Matrix
- Define an **affinity matrix A**, where:
  - \( A(i, j) = exp(-||I(i) - I(j)||^2 / \sigma^2) \) if pixels i and j are neighbors (left, right, top, or down).
  - Otherwise, \( A(i, j) = 0 \).
- Use **σ = 0.1** to control the weight decay of similarity.

### 3. Spectral Clustering Algorithm
- Compute the **Laplacian matrix** of the affinity matrix.
- Use **sparse matrices and sparse SVD** (e.g., `scipy.sparse.linalg.svds`) to improve computational efficiency.
- Perform clustering using eigenvectors derived from the Laplacian matrix.

### 4. Visualization and Results
#### a) Displaying the Clustering with 10 Clusters
- Cluster the image pixels into **10 clusters**.
- Generate an **82 × 128 label image**, where each pixel is assigned a cluster label.
- Display the clustered image.

#### b) Reconstructing the Image with Cluster Averages
- Compute the **mean RGB values** of pixels in each cluster.
- Assign these mean values to all pixels in the corresponding cluster.
- Display the new colorized image representing the clustered regions.

#### c) Repeating the Process for 20 Clusters
- Perform the same steps as above with **20 clusters**.
- Display both the **cluster label image** and the **color-reconstructed image**.

## How to Run
1. Load the `scene2.jpg` image into the project directory.
2. Execute the script to perform spectral clustering with 10 and 20 clusters.
3. The output will display:
   - The clustered label images for both cases.
   - The reconstructed images using mean RGB values per cluster.

## Dependencies
- Python (>=3.7)
- NumPy
- SciPy (`scipy.sparse` for efficient computations)
- Matplotlib (for visualization)
- OpenCV or PIL (for image handling)

## Applications
Spectral clustering is widely used in:
- Image segmentation
- Object detection
- Medical image analysis
- Pattern recognition

This assignment demonstrates how unsupervised clustering techniques can be used to segment images into meaningful regions based on pixel similarities.
