# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

**Step 1:**       
Read the image and convert to grayscale.        
**Step 2:**       
(Optional) Apply Gaussian blur to reduce noise.        
**Step 3:**      
Apply global thresholding (Binary, Binary Inverse, To Zero, To Zero-Inverse, Truncate).       
**Step 4:**      
Apply Otsu’s and adaptive thresholding (Mean and Gaussian).      
**Step 5:**      
Display and compare the original and thresholded images.

## Program

```py
# Load the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
```py
# Read the Image and convert to grayscale
image_gray = cv2.imread("duck.jpg", 0)
```
```py
# Use Global thresholding to segment the image
ret, thresh_dipt1 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY)
ret, thresh_dipt2 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY_INV)
ret, thresh_dipt3 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO)
ret, thresh_dipt4 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO_INV)
ret, thresh_dipt5 = cv2.threshold(image_gray, 100, 255, cv2.THRESH_TRUNC)
```
```py

# Use Adaptive thresholding to segment the image & Otsu's method
ret, thresh_dipt6 = cv2.threshold(image_gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU
thresh_dipt7 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
thresh_dipt8 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)
```
```py
# Titles and images
titles = ["Gray Image",
          "Threshold (Binary)",
          "Threshold (Binary Inverse)",
          "Threshold (To Zero)",
          "Threshold (To Zero-Inverse)",
          "Threshold (Truncate)",
          "Otsu",
          "Adaptive Threshold (Mean)",
          "Adaptive Threshold (Gaussian)"]

images = [image_gray, thresh_dipt1, thresh_dipt2, thresh_dipt3, thresh_dipt4, thresh_dipt5, thresh_dipt6, thresh_dipt7, thresh_dipt8]
```
```py
# Display results
for i in range(0, 9):
    plt.figure(figsize=(10, 10))
    plt.subplot(1, 2, 1)
    plt.title("Original Image")
    plt.imshow(image_gray, cmap='gray')
    plt.axis("off")
    
    plt.subplot(1, 2, 2)
    plt.title(titles[i])
    plt.imshow(images[i], cmap='gray')
    plt.axis("off")
    
    plt.show()

```
## Output

### Original Image
<img width="704" height="238" alt="image" src="https://github.com/user-attachments/assets/34dd5e2d-8736-4ca8-aab3-152f78a85a41" />


### Global Thresholding
<img width="682" height="724" alt="image" src="https://github.com/user-attachments/assets/32a8f2fc-1a6a-465a-b00e-0f548194e785" />
<img width="716" height="484" alt="image" src="https://github.com/user-attachments/assets/cc43c29b-236e-48d3-a10e-389e7bf1fdc2" />


### Adaptive Thresholding
<img width="687" height="490" alt="image" src="https://github.com/user-attachments/assets/d3f4216d-94c7-473e-b828-53834e96082a" />


### Optimum Global Thesholding using Otsu's Method
<img width="696" height="242" alt="image" src="https://github.com/user-attachments/assets/7d17187f-3a0c-4672-92ea-046b01cab55f" />



## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
