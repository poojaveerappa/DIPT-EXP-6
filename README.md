### Edge Detection Using OpenCV

## Aim

To perform edge detection using **Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors**.

---

## Software Required

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

---

## Algorithm

1. Import all the necessary libraries such as OpenCV, NumPy, and Matplotlib.

2. Load the input image using `cv2.imread()`.

3. Convert the input image into grayscale using `cv2.cvtColor()`.

4. Apply the **Sobel operator** using `cv2.Sobel()` to detect horizontal and vertical edges.

5. Apply the **Prewitt operator** using custom horizontal and vertical kernels.

6. Apply the **Roberts operator** using custom diagonal kernels to detect edges.

7. Apply the **Laplacian operator** using `cv2.Laplacian()` to detect rapid intensity changes.

8. Apply the **Canny edge detector** using `cv2.Canny()` to obtain clear and thin edges.

9. Display all the edge-detected images using Matplotlib for comparison.

---

## Developed By

- **Name:** POOJA V
- **Register No:** 212225040302
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread("lily.png")
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Convert to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)

# 1. Sobel Edge Detection
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.magnitude(sobel_x, sobel_y)
sobel = cv2.convertScaleAbs(sobel)

# 2. Prewitt Edge Detection
kernel_x = np.array([[-1, 0, 1],
                     [-1, 0, 1],
                     [-1, 0, 1]])

kernel_y = np.array([[-1, -1, -1],
                     [ 0,  0,  0],
                     [ 1,  1,  1]])

prewitt_x = cv2.filter2D(gray, cv2.CV_32F, kernel_x)
prewitt_y = cv2.filter2D(gray, cv2.CV_32F, kernel_y)

prewitt = cv2.magnitude(prewitt_x, prewitt_y)
prewitt = cv2.convertScaleAbs(prewitt)

# 3. Roberts Edge Detection
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

rx = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
ry = cv2.filter2D(gray, cv2.CV_32F, roberts_y)

roberts = cv2.magnitude(rx, ry)
roberts = cv2.convertScaleAbs(roberts)

# 4. Laplacian Edge Detection
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

# 5. Canny Edge Detection
canny = cv2.Canny(gray, 100, 200)

# Display all outputs
plt.figure(figsize=(12, 9))

plt.subplot(2, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2, 3, 2)
plt.imshow(sobel, cmap="gray")
plt.title("Sobel Edge Detection")
plt.axis("off")

plt.subplot(2, 3, 3)
plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt Edge Detection")
plt.axis("off")

plt.subplot(2, 3, 4)
plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")

plt.subplot(2, 3, 5)
plt.imshow(laplacian, cmap="gray")
plt.title("Laplacian Edge Detection")
plt.axis("off")

plt.subplot(2, 3, 6)
plt.imshow(canny, cmap="gray")
plt.title("Canny Edge Detection")
plt.axis("off")

plt.tight_layout()
plt.show()
```
---

## Output

<img width="342" height="272" alt="image" src="https://github.com/user-attachments/assets/9c1d3597-f62f-4209-8eb0-01d58fe1c1c2" />

### 1. Sobel Edge Detector

- Detects edges in horizontal and vertical directions.
- Produces a gradient-based edge map.

<img width="341" height="277" alt="image" src="https://github.com/user-attachments/assets/0ac55288-d1d8-4dd9-9ddb-48911ba2a886" />

### 2. Prewitt Edge Detector

- Uses simple directional kernels.
- Detects horizontal and vertical edges.

 <img width="346" height="280" alt="image" src="https://github.com/user-attachments/assets/4452c046-eb8f-4203-9ad4-f3ce9887765d" />


### 3. Roberts Edge Detector

- Detects edges using diagonal gradients.
- Sensitive to noise.

<img width="350" height="275" alt="image" src="https://github.com/user-attachments/assets/92c56f89-f397-4951-a9ac-2782969fd430" />

### 4. Laplacian Edge Detector

- Uses second-order derivatives.
- Highlights rapid intensity changes.

<img width="342" height="271" alt="image" src="https://github.com/user-attachments/assets/13b14e36-4863-4342-9d9c-d56dcf4e7257" />

### 5. Canny Edge Detector

- Uses a multi-stage edge detection process.
- Produces clean and thin edges.

<img width="338" height="282" alt="image" src="https://github.com/user-attachments/assets/47ee0efd-d225-400e-a136-9425dcc1d870" />

---

## Result

Thus, edges are successfully detected using **Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques**. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and image analysis.
