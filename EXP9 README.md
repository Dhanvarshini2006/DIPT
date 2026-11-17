# Implementation of Erosion and Dilation Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological operations such as Erosion and Dilation on an image.

The program performs the following operations:

- Image Erosion
- Image Dilation

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

Create a blank image using NumPy.

### Step 3:

Insert text onto the image using OpenCV's text drawing function.

### Step 4:

Display the original image.

### Step 5:

Create a structuring element (kernel) of suitable size.

### Step 6: Image Erosion

- Apply the erosion operation using the created kernel.
- Remove pixels from the boundaries of foreground objects.
- Display the eroded image.

### Step 7: Image Dilation

- Apply the dilation operation using the same kernel.
- Add pixels to the boundaries of foreground objects.
- Display the dilated image.

### Step 8:

Compare the original, eroded, and dilated images.

## Program

## Developed By

**Name:**DHAN VARSHINI J P

**Register No:** 212224230055
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Create a blank image
img = np.zeros((300, 500), dtype=np.uint8)

# Insert text into the image
cv2.putText(img, 'DHAN VARSHINI', (30, 150),
            cv2.FONT_HERSHEY_SIMPLEX, 1, 255, 3)

# Display original image
plt.figure(figsize=(12, 5))

plt.subplot(1, 3, 1)
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.axis('off')

# Create structuring element (kernel)
kernel = np.ones((5, 5), np.uint8)

# Image Erosion
erosion = cv2.erode(img, kernel, iterations=1)

plt.subplot(1, 3, 2)
plt.imshow(erosion, cmap='gray')
plt.title('Eroded Image')
plt.axis('off')

# Image Dilation
dilation = cv2.dilate(img, kernel, iterations=1)

plt.subplot(1, 3, 3)
plt.imshow(dilation, cmap='gray')
plt.title('Dilated Image')
plt.axis('off')

# Display all images
plt.tight_layout()
plt.show()

```

## Output

### Original Image

- A text image containing characters is displayed.
- The image serves as the input for morphological processing.

<img width="416" height="270" alt="image" src="https://github.com/user-attachments/assets/d80effc5-6650-485b-a816-2e70704a02de" />


### Erosion

- Original image is displayed.
- Eroded image is displayed.
- The thickness of the characters is reduced.
- Object boundaries shrink inward.
<img width="398" height="262" alt="image" src="https://github.com/user-attachments/assets/e9b7d3f7-238e-43fa-b4a8-c30d34dccc30" />


### Dilation

- Original image is displayed.
- Dilated image is displayed.
- The thickness of the characters increases.
- Object boundaries expand outward.
<img width="398" height="265" alt="image" src="https://github.com/user-attachments/assets/053082df-fde4-4e93-afef-ece310f4ea5a" />


## Result

Thus, the morphological operations **Erosion** and **Dilation** are successfully implemented using OpenCV.
