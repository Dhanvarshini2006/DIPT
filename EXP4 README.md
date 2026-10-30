# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:

### Name:DHAN VARSHINI J P  

### Register No: 212224230055

```

import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('Sunflower-1-771x1024.webp')

if img is None:
    print("Image not found")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    h, w = img.shape[:2]

    M = np.float32([[1, 0, 50], [0, 1, 80]])
    translated = cv2.warpAffine(img, M, (w, h))

    down = cv2.resize(img, None, fx=0.5, fy=0.5)
    up = cv2.resize(img, None, fx=2, fy=2)

    H = np.float32([[1, 0.5, 0], [0, 1, 0]])
    horizontal = cv2.warpAffine(img, H, (w, h))

    V = np.float32([[1, 0, 0], [0.5, 1, 0]])
    vertical = cv2.warpAffine(img, V, (w, h))

    flip_h = cv2.flip(img, 1)
    flip_v = cv2.flip(img, 0)
    flip_b = cv2.flip(img, -1)

    center = (w // 2, h // 2)
    R1 = cv2.getRotationMatrix2D(center, 45, 1)
    rotate45 = cv2.warpAffine(img, R1, (w, h))

    R2 = cv2.getRotationMatrix2D(center, 90, 1)
    rotate90 = cv2.warpAffine(img, R2, (w, h))

    images = [img, translated, down, up, horizontal,
              vertical, flip_h, flip_v, flip_b,
              rotate45, rotate90]

    titles = ['Original', 'Translation', 'Downscaling',
              'Upscaling', 'Horizontal Shearing',
              'Vertical Shearing', 'Horizontal Reflection',
              'Vertical Reflection', 'Both Axis Reflection',
              'Rotation 45 Degree', 'Rotation 90 Degree']

    plt.figure(figsize=(15, 12))

    for i in range(len(images)):
        plt.subplot(3, 4, i + 1)
        plt.imshow(images[i])
        plt.title(titles[i])
        plt.axis('off')

    plt.tight_layout()
    plt.show()
```


---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed

  <img width="341" height="390" alt="image" src="https://github.com/user-attachments/assets/c7f99c07-6aea-402b-9d90-f5b38788e336" />
 

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed

<img width="672" height="392" alt="image" src="https://github.com/user-attachments/assets/2b507e2d-7d1e-46bf-be1e-1d53f1edd3da" />


### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed

<img width="670" height="402" alt="image" src="https://github.com/user-attachments/assets/2f5a656e-4c43-40df-a724-39a2e61fe7d7" />


### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed
<img width="657" height="387" alt="image" src="https://github.com/user-attachments/assets/a3e9500e-91f2-4394-ba75-f19f2f17181f" />


### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed

<img width="1027" height="395" alt="image" src="https://github.com/user-attachments/assets/53b08048-4bc9-483c-ac12-1e67256500fc" />


---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.

