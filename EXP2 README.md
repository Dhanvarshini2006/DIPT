# Image Capture and Video Processing Using OpenCV

---

## Aim

To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1. Write the frame as a JPG file  
2. Display the video  
3. Display the video by resizing the window  
4. Rotate and display the video  

---

## 🛠️ Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  

---

## ⚙️ Algorithm

### Step 1:
Import the required libraries and initialize the webcam using `cv2.VideoCapture()`.

### Step 2:
Capture frames continuously from the webcam.

### Step 3:
Save a frame as a JPG image using `cv2.imwrite()`.

### Step 4:
Display the live video stream using `cv2.imshow()`.

### Step 5:
Resize the frame and rotate it using OpenCV functions, then display the processed frames.

---

## 💻 Program

### Developed By:
**Name:** DHAN VARSHINI J P

### Register No: 212224230055

```
import cv2

cap = cv2.VideoCapture(0)

if not cap.isOpened():
    print("Error: Cannot open webcam")
    exit()

saved = False

while True:
    ret, frame = cap.read()

    if not ret:
        print("Error: Cannot capture frame")
        break

    if not saved:
        cv2.imwrite("captured_image.jpg", frame)
        print("Captured image is saved as captured_image.jpg")
        saved = True

    cv2.imshow("Live Webcam Video", frame)

    resized_frame = cv2.resize(frame, (640, 480))
    cv2.imshow("Resized Video (640 x 480)", resized_frame)

    rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    cv2.imshow("Rotated Video (90 Degrees Clockwise)", rotated_frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```


---

## Output

### i) Write the frame as JPG image
Captured image is saved as `captured_image.jpg`

### ii) Display the video
Live webcam video is displayed

### iii) Display the video by resizing the window
Video is shown in resized resolution (640 × 480)

### iv) Rotate and display the video
Video is displayed after rotation (90° clockwise)

---
<img width="791" height="597" alt="Screenshot 2026-10-28 090703" src="https://github.com/user-attachments/assets/fde27974-17c9-41c3-a206-b1752d6abd92" />
<img width="602" height="801" alt="Screenshot 2026-10-28 090720" src="https://github.com/user-attachments/assets/80cb5f3d-4e40-40a8-bd93-e75cf400f2d1" />
<img width="796" height="600" alt="Screenshot 2026-10-28 090733" src="https://github.com/user-attachments/assets/1393c818-2cb9-4bca-99b4-ca98d551d938" />


## Result

Thus, the image is successfully captured from the webcam and various video processing operations such as saving, displaying, resizing, and rotating are performed using OpenCV.

