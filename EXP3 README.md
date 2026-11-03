# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program

### Developed By:
**Name:** DHAN VARSHINI J P


**RegisterNo:** 212224230055
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Import required libraries

# Step 2: Read image in grayscale
gray = cv2.imread('Sunflower-1-771x1024.webp', cv2.IMREAD_GRAYSCALE)

if gray is None:
    raise FileNotFoundError("file not found")

# Step 3: Display grayscale image and histogram
plt.figure(figsize=(12, 8))
plt.subplot(2, 2, 1)
plt.imshow(gray, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(gray.ravel(), 256, [0, 256], color='black')
plt.title('Grayscale Histogram')

# Step 4: Histogram equalization
equalized = cv2.equalizeHist(gray)

# Step 5: Display original and enhanced grayscale images
plt.subplot(2, 2, 3)
plt.imshow(equalized, cmap='gray')
plt.title('Enhanced Grayscale Image')
plt.axis('off')

plt.subplot(2, 2, 4)
plt.hist(equalized.ravel(), 256, [0, 256], color='black')
plt.title('Enhanced Grayscale Histogram')
plt.tight_layout()
plt.show()

# Step 6: Read image in color
color = cv2.imread('Sunflower-1-771x1024.webp', cv2.IMREAD_COLOR)

# Convert BGR to RGB for displaying correctly
rgb = cv2.cvtColor(color, cv2.COLOR_BGR2RGB)

# Step 7: Split B, G, R channels and plot histograms
b, g, r = cv2.split(color)

plt.figure(figsize=(12, 4))
for i, (channel, name, col) in enumerate([
    (b, 'Blue Histogram', 'blue'),
    (g, 'Green Histogram', 'green'),
    (r, 'Red Histogram', 'red')
]):
    plt.subplot(1, 3, i + 1)
    plt.hist(channel.ravel(), 256, [0, 256], color=col)
    plt.title(name)

plt.tight_layout()
plt.show()

# Step 8: Convert BGR to HSV
hsv = cv2.cvtColor(color, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)

# Step 9: Equalize the V channel
v_equalized = cv2.equalizeHist(v)

# Step 10: Merge channels and convert back to BGR
enhanced_hsv = cv2.merge((h, s, v_equalized))
enhanced_color = cv2.cvtColor(enhanced_hsv, cv2.COLOR_HSV2BGR)
enhanced_rgb = cv2.cvtColor(enhanced_color, cv2.COLOR_BGR2RGB)

# Step 11: Display original and enhanced color images and histograms
plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(rgb)
plt.title('Original Color Image')
plt.axis('off')

plt.subplot(2, 2, 2)
for channel, col in zip((r, g, b), ('red', 'green', 'blue')):
    plt.hist(channel.ravel(), 256, [0, 256], color=col, alpha=0.5)
plt.title('Original Color Histogram')

plt.subplot(2, 2, 3)
plt.imshow(enhanced_rgb)
plt.title('Enhanced Color Image')
plt.axis('off')

plt.subplot(2, 2, 4)
er, eg, eb = cv2.split(enhanced_rgb)
for channel, col in zip((er, eg, eb), ('red', 'green', 'blue')):
    plt.hist(channel.ravel(), 256, [0, 256], color=col, alpha=0.5)
plt.title('Enhanced Color Histogram')

plt.tight_layout()
plt.show()
```
---

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---
<img width="1012" height="740" alt="image" src="https://github.com/user-attachments/assets/e22e75ac-8871-498b-af86-bcf4aa0b5b10" />
<img width="1360" height="546" alt="image" src="https://github.com/user-attachments/assets/84d38658-6e99-4d07-ba16-9374dcd464e3" />

<img width="975" height="737" alt="image" src="https://github.com/user-attachments/assets/5fbcb93c-0d77-4e3c-94ba-05079d9e1873" />



## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.

