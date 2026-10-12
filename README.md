# computer-vision-assignments[README.md](https://github.com/user-attachments/files/33347598/README.md)
# Computer Vision Assignments

Two assignments from the Computer Vision course at IIT Jodhpur.

## 1. Interactive Image Segmentation via Graph Cut
`graphcut_segmentation/graphcut_segmentation.ipynb`

Scribble-based foreground/background segmentation formulated as energy minimisation and solved with **min-cut/max-flow** (PyMaxflow).

- Green scribbles = foreground seeds, blue scribbles = background seeds
- Region costs from **5-component Gaussian Mixture Models** in LAB colour space
- Contrast-sensitive n-link weights on a 4-connected pixel graph, hard seed constraints
- **Iterative GMM re-fitting** (5 rounds) for sharper colour models
- Post-processing: morphological opening/closing, hole filling, Gaussian boundary smoothing
- Compared against **Otsu thresholding** and **K-Means** baselines

**Run:** open in Google Colab. The notebook asks you to upload the original images and matching scribble images (sample files are in `graphcut_segmentation/images/`).

## 2. Panorama Stitching
`panorama_stitching/panorama_stitching.ipynb`

Stitches three overlapping images into a panorama with the center image as reference.

- **SIFT** feature extraction
- Brute-force matching with **Lowe's ratio test** (0.75)
- **RANSAC homography** estimation
- Warping onto a common canvas, naive overlay vs **distance-transform feathered blending**
- Automatic black-border cropping

**Run:** put `left.jpeg`, `center.jpeg`, `right.jpeg` next to the notebook (samples in `panorama_stitching/images/`) and run all cells.

## Requirements
```
pip install opencv-python numpy matplotlib scikit-learn scipy PyMaxflow ipywidgets
```

## Results
Add before/after images here, e.g.:

![Panorama](panorama_stitching/images/panorama_result.png)
![Graph cut comparison](graphcut_segmentation/images/comparison_img1.png)
