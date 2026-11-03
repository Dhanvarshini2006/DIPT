# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** DHAN VARSHINI J P
- **Register Number:** 212224230055
- 
```

from tkinter import Tk, filedialog
from PIL import Image
import numpy as np
import matplotlib.pyplot as plt

root = Tk()
root.withdraw()
root.attributes("-topmost", True)

file_path = filedialog.askopenfilename(
    title="Choose an Image",
    filetypes=[
        ("Image Files", "*.png *.jpg *.jpeg *.bmp")
    ]
)

root.destroy()

if file_path:
    img = Image.open(file_path).convert("RGB--")
    rgb_matrix = np.array(img)

    print("Original RGB Matrix:")
    print(rgb_matrix) 
    print("Matrix Shape:", rgb_matrix.shape)

    brightness = float(input("Enter brightness value (e.g., 1.5 brighter, 0.5 darker): "))

    if brightness < 0:
        print("Brightness must be zero or greater.")
    else:
        bright_matrix = np.clip(
            rgb_matrix.astype(np.float32) * brightness,
            0,
            255
        ).astype(np.uint8)

        bright_img = Image.fromarray(bright_matrix)

        plt.figure(figsize=(12, 5))

        plt.subplot(1, 2, 1)
        plt.imshow(img)
        plt.title("Original Image")
        plt.axis("off")

        plt.subplot(1, 2, 2)
        plt.imshow(bright_img)
        plt.title("Brightness Changed")
        plt.axis("off")

        plt.show()

        print("Brightness-Changed RGB Matrix:")
        print(bright_matrix)

        save_path = filedialog.asksaveasfilename(
            title="Save Brightness-Changed Image",
            defaultextension=".png",
            filetypes=[("PNG Image", "*.png"), ("JPEG Image", "*.jpg")]
        )

        if save_path:
            bright_img.save(save_path)
            print("Image saved successfully:", save_path)
        else:
            print("Image was not saved.")
else:
    print("No image selected.")

```


## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.

<img width="313" height="561" alt="image" src="https://github.com/user-attachments/assets/3901acba-dcaf-4605-9ffe-1112b5b24054" />
<img width="1272" height="627" alt="image" src="https://github.com/user-attachments/assets/19c3b1f6-236f-4be7-a52d-751f6598d4ea" />
<img width="165" height="537" alt="image" src="https://github.com/user-attachments/assets/bde0248e-bcf8-4cf9-932f-5a8cd8415b03" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.


