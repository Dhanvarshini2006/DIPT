# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Load the input image using OpenCV.

### Step 3:

Convert the input image into grayscale format.

### Step 4: Global Thresholding

- Select a fixed threshold value.
- Apply thresholding to separate foreground and background pixels.
- Display the thresholded image.

### Step 5: Adaptive Thresholding

- Compute threshold values for small regions of the image.
- Apply Adaptive Mean Thresholding.
- Apply Adaptive Gaussian Thresholding.
- Display the segmented images.

### Step 6: Otsu's Thresholding

- Automatically determine the optimal threshold value.
- Apply Otsu's thresholding technique.
- Display the segmented image.

### Step 7:

Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods.

## Program

## Developed By

**Name:** DHAN VARSHINI J P

**Register No:** 212224230055

```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load input image
img = cv2.imread('Sunflower-1-771x1024.webp')

# Convert image into grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Global Thresholding
ret, global_thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)

# Adaptive Mean Thresholding
adaptive_mean = cv2.adaptiveThreshold(
    gray, 255,
    cv2.ADAPTIVE_THRESH_MEAN_C,
    cv2.THRESH_BINARY,
    11, 2
)

# Adaptive Gaussian Thresholding
adaptive_gaussian = cv2.adaptiveThreshold(
    gray, 255,
    cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
    cv2.THRESH_BINARY,
    11, 2
)

# Otsu's Thresholding
ret, otsu_thresh = cv2.threshold(
    gray, 0, 255,
    cv2.THRESH_BINARY + cv2.THRESH_OTSU
)

# Display all results
titles = [
    'Original Image',
    'Grayscale Image',
    'Global Thresholding',
    'Adaptive Mean Thresholding',
    'Adaptive Gaussian Thresholding',
    "Otsu's Thresholding"
]

images = [
    cv2.cvtColor(img, cv2.COLOR_BGR2RGB),
    gray,
    global_thresh,
    adaptive_mean,
    adaptive_gaussian,
    otsu_thresh
]

plt.figure(figsize=(12, 8))

for i in range(6):
    plt.subplot(2, 3, i + 1)
    plt.imshow(images[i], cmap='gray' if i != 0 else None)
    plt.title(titles[i])
    plt.axis('off')

plt.tight_layout()
plt.show()

# Display threshold values
print("Global Threshold Value:", 127)
print("Otsu Threshold Value:", ret)

```
## Output

### Original Grayscale Image

- The grayscale version of the input image is displayed.
- Serves as the input for thresholding operations.

  <img width="682" height="388" alt="image" src="https://github.com/user-attachments/assets/8975add7-2972-4751-aee2-58323ef90ced" />


### Global Thresholding

- Original image is displayed.
- Thresholded image is displayed.
- A fixed threshold value is used for segmentation.
- Pixels are classified as foreground or background.

  <img width="348" height="395" alt="image" src="https://github.com/user-attachments/assets/6dcb8fa1-94e7-430f-9263-22e4c6e1fc9c" />


### Adaptive Thresholding

- Original image is displayed.
- Adaptive Mean Thresholded image is displayed.
- Adaptive Gaussian Thresholded image is displayed.
- Threshold values vary across different regions of the image.
- Suitable for images with uneven illumination.

<img width="680" height="447" alt="image" src="https://github.com/user-attachments/assets/a97a40f0-0999-4584-b906-4ebd9b268a46" />


### Otsu's Thresholding

- Original image is displayed.
- Otsu segmented image is displayed.
- Optimal threshold value is calculated automatically.
- Produces improved segmentation for bimodal histograms.

  <img width="337" height="400" alt="image" src="https://github.com/user-attachments/assets/8bc59f43-c345-4f7e-b2c8-246b28fe8375" />



## Result

Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV. 
