# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** DHAN VARSHINI J P 
- **Register No:** 212224230055

```

import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('Sunflower-1-771x1024.webp')

if img is None:
    print("Image not found")
else:
    rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    avg = cv2.blur(img, (5, 5))

    kernel = np.array([[1, 2, 1],
                       [2, 4, 2],
                       [1, 2, 1]], dtype=np.float32) / 16
    weighted = cv2.filter2D(img, -1, kernel)

    gaussian = cv2.GaussianBlur(img, (5, 5), 0)

    median = cv2.medianBlur(img, 5)

    sharp_kernel = np.array([[0, -1, 0],
                             [-1, 5, -1],
                             [0, -1, 0]])
    sharpened = cv2.filter2D(img, -1, sharp_kernel)

    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian = cv2.convertScaleAbs(laplacian)

    images = [rgb,
              cv2.cvtColor(avg, cv2.COLOR_BGR2RGB),
              cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB),
              cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB),
              cv2.cvtColor(median, cv2.COLOR_BGR2RGB),
              cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB),
              gray,
              laplacian]

    titles = ['Original Image', 'Averaging Filter',
              'Weighted Averaging Filter', 'Gaussian Filter',
              'Median Filter', 'Laplacian Sharpening',
              'Grayscale Image', 'Laplacian Operator']

    plt.figure(figsize=(14, 10))

    for i in range(8):
        plt.subplot(2, 4, i + 1)
        plt.imshow(images[i], cmap='gray' if i >= 6 else None)
        plt.title(titles[i])
        plt.axis('off')

    plt.tight_layout()
    plt.show()

```

---

##  Output

<img width="1345" height="907" alt="image" src="https://github.com/user-attachments/assets/8dfa6eb6-5326-4245-90e9-e1f2be31e9a3" />

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.

