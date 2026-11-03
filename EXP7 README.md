#  Lane Detection

##  Aim

To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

---

## Learning Objective

* Understand each stage of image processing
* Learn how to build a complete computer vision pipeline
* Practice writing code in guided sections



---

##  Software Used

* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

---

##  Algorithm & Explanation

---

1. Import OpenCV, NumPy and Matplotlib libraries.
2. Read the input image and convert it into grayscale.
3. Display the original and grayscale images.
4. Apply thresholding and ROI masking to select the road region.
5. Perform Canny edge detection, Gaussian blur and Hough Transform to detect lane lines.
6. Draw the detected lane lines on the original image and display the final output.

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Import Libraries

# Step 2: Read the Image
image = cv2.imread('road image.webp')

if image is None:
    print("Error: Image not found. Check the image path.")

else:
    # Step 3: Convert to Grayscale
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # Step 4: Display Images
    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(gray, cmap='gray')
    plt.title("Grayscale Image")
    plt.axis("off")
    plt.show()

    # Step 5: Thresholding
    threshold = cv2.threshold(gray, 150, 255, cv2.THRESH_BINARY)[1]

    plt.imshow(threshold, cmap='gray')
    plt.title("Thresholded Image")
    plt.axis("off")
    plt.show()

    # Step 6: Region of Interest (ROI)
    height, width = gray.shape

    mask = np.zeros_like(gray)

    polygon = np.array([[
        (0, height),
        (width, height),
        (width, int(height * 0.6)),
        (0, int(height * 0.6))
    ]], dtype=np.int32)

    cv2.fillPoly(mask, polygon, 255)

    roi = cv2.bitwise_and(threshold, mask)

    plt.imshow(roi, cmap='gray')
    plt.title("ROI Masked Image")
    plt.axis("off")
    plt.show()

    # Step 7: Edge Detection (Canny)
    edges = cv2.Canny(roi, 50, 150)

    plt.imshow(edges, cmap='gray')
    plt.title("Edge Detected Image")
    plt.axis("off")
    plt.show()

    # Step 8: Gaussian Blur
    blurred = cv2.GaussianBlur(edges, (5, 5), 0)

    plt.imshow(blurred, cmap='gray')
    plt.title("Smoothed Image")
    plt.axis("off")
    plt.show()

    # Step 9: Hough Transform
    lines = cv2.HoughLinesP(
        blurred,
        rho=1,
        theta=np.pi / 180,
        threshold=50,
        minLineLength=50,
        maxLineGap=100
    )

    line_image = np.zeros_like(image)

    if lines is not None:
        lines = np.asarray(lines).reshape(-1, 4)

        for x1, y1, x2, y2 in lines:
            cv2.line(
                line_image,
                (int(x1), int(y1)),
                (int(x2), int(y2)),
                (0, 255, 0),
                5
            )

    plt.imshow(cv2.cvtColor(line_image, cv2.COLOR_BGR2RGB))
    plt.title("Detected Lines")
    plt.axis("off")
    plt.show()

    # Step 10: Lane Detection Logic
    final_image = cv2.addWeighted(image, 0.8, line_image, 1, 0)

    plt.figure(figsize=(10, 6))
    plt.imshow(cv2.cvtColor(final_image, cv2.COLOR_BGR2RGB))
    plt.title("Final Lane Detection Output")
    plt.axis("off")
    plt.show()
```

---

##  Expected Output

* Original image
* Grayscale image
* Thresholded image

  <img width="772" height="798" alt="image" src="https://github.com/user-attachments/assets/f4a4a089-dcb3-426b-87a9-f44b383803e0" />

* ROI masked image
* Edge detected image

 <img width="295" height="783" alt="image" src="https://github.com/user-attachments/assets/ed297e64-f485-45c1-b82b-b3125fa1f765" />

* Smoothed image
* Detected lines

  <img width="333" height="792" alt="image" src="https://github.com/user-attachments/assets/e7b430a8-6114-4d28-907d-fe9a25efbc2c" />

* Final lane detection output

  <img width="360" height="482" alt="image" src="https://github.com/user-attachments/assets/a461752d-9b46-4a78-b3b6-7ab14cd18450" />


---



## Result

Thus, the lane detection pipeline is successfully implemented by completing the missing code sections. The system detects and highlights lane lines effectively.

---

##  Developed By

* **Name:** DHAN VARSHINI J P
* **Register No:** 212224230055
