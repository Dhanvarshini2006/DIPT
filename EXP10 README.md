# Opening and Closing Operations Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

- Morphological Opening
- Morphological Closing

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

Create or load an input image containing foreground objects.

### Step 3:

Display the original image.

### Step 4:

Create a structuring element (kernel) of suitable size.

### Step 5: Opening Operation

- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving the shape of larger objects.
- Display the opened image.

### Step 6: Closing Operation

- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

### Step 7:

Compare the original, opened, and closed images.

## Program

## Developed By

**Name:** DHAN VARSHINI J P

**Register No:** 212224230055

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load the input image
img = cv2.imread('image.jpg', 0)

# Display original image
plt.subplot(1, 3, 1)
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.axis('off')

# Create structuring element
kernel = np.ones((5, 5), np.uint8)

# Opening operation (Erosion followed by Dilation)
opening = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)

# Display opened image
plt.subplot(1, 3, 2)
plt.imshow(opening, cmap='gray')
plt.title('Opening')
plt.axis('off')

# Closing operation (Dilation followed by Erosion)
closing = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)

# Display closed image
plt.subplot(1, 3, 3)
plt.imshow(closing, cmap='gray')
plt.title('Closing')
plt.axis('off')

# Show all images
plt.show()
```

## Output

### Original Image

- The input image is displayed.
- The image serves as the source for morphological processing.

<img width="347" height="395" alt="image" src="https://github.com/user-attachments/assets/9148df1d-82b4-4613-8175-9b64201dcf26" />


### Opening Operation

- Original image is displayed.
- Opened image is displayed.
- Small foreground noise is removed.
- Thin protrusions and isolated pixels are eliminated.
- Object boundaries become smoother.

<img width="340" height="398" alt="image" src="https://github.com/user-attachments/assets/350ba213-73ec-4cdc-afff-aeb3c03b8ecc" />


### Closing Operation

- Original image is displayed.
- Closed image is displayed.
- Small holes and gaps inside objects are filled.
- Broken regions are connected.
- Object boundaries become more continuous.
  
<img width="351" height="390" alt="image" src="https://github.com/user-attachments/assets/f0db9bcd-f2e3-4069-8826-7a42cb9937ee" />


## Applications

### Opening

- Noise removal in binary images.
- Separation of connected objects.
- Preprocessing for object detection.

### Closing

- Filling small holes in objects.
- Connecting nearby components.
- Enhancing segmented regions.

## Advantages

### Opening

- Removes unwanted foreground noise.
- Preserves major object structures.
- Improves segmentation quality.

### Closing

- Restores object continuity.
- Eliminates small background gaps.
- Improves object representation.

## Result

Thus, the morphological operations **Opening** and **Closing** are successfully implemented using OpenCV. 
