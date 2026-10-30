# Geometric Transformations Using OpenCV

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

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

##  Program

### Developed By:
# Name: Vijiyalakshmi A
### Register No: 212225240185  

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read image
img = cv2.imread("rabbit.jpg")

if img is None:
    print("Image not found! Check the filename.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    h, w = img.shape[:2]

    # Step 2: Image Translation
    M = np.float32([[1, 0, 50],
                    [0, 1, 80]])
    translated = cv2.warpAffine(img, M, (w, h))

    # Step 3: Image Scaling
    downscaled = cv2.resize(img, None, fx=1.0, fy=0.5)
    upscaled = cv2.resize(img, None, fx=3, fy=4)

    # Step 4: Image Shearing
    horizontal_matrix = np.float32([
        [1, 0.5, 0],
        [0, 1, 0]
    ])

    vertical_matrix = np.float32([
        [1, 0, 0],
        [0.5, 1, 0]
    ])

    horizontal_shear = cv2.warpAffine(
        img, horizontal_matrix, (w, h))
    vertical_shear = cv2.warpAffine(
        img, vertical_matrix, (w, h))

    # Step 5: Image Reflection
    horizontal_flip = cv2.flip(img, 1)
    vertical_flip = cv2.flip(img, 0)
    both_flip = cv2.flip(img, -1)

    # Step 6: Image Rotation
    center = (w // 2, h // 2)

    M45 = cv2.getRotationMatrix2D(center, 45, 1)
    rotated45 = cv2.warpAffine(img, M45, (w, h))

    M90 = cv2.getRotationMatrix2D(center, 90, 1)
    rotated90 = cv2.warpAffine(img, M90, (w, h))

    # Step 7: Display results
    titles = [
        "Original", "Translation",
        "Downscale 0.5x", "Upscale 2x",
        "Horizontal Shear", "Vertical Shear",
        "Horizontal Reflection", "Vertical Reflection",
        "Both Axes Reflection", "Rotation 45 Degrees",
        "Rotation 90 Degrees"
    ]

    images = [
        img, translated,
        downscaled, upscaled,
        horizontal_shear, vertical_shear,
        horizontal_flip, vertical_flip,
        both_flip, rotated45, rotated90
    ]

    plt.figure(figsize=(15, 14))

    for i in range(len(images)):
        plt.subplot(4, 3, i + 1)
        plt.imshow(images[i])
        plt.title(titles[i])
        plt.axis("off")

    plt.tight_layout()
    plt.show()

```
##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed

<img width="198" height="280" alt="Screenshot 2026-10-30 221537" src="https://github.com/user-attachments/assets/95ab331a-9dfb-4f60-9f36-2495eb4c68d6" /><img width="225" height="287" alt="Screenshot 2026-10-30 221210" src="https://github.com/user-attachments/assets/7c74ff87-aa38-400d-b91f-266e7b04a67c" />

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed
<img width="198" height="280" alt="Screenshot 2026-10-30 221537" src="https://github.com/user-attachments/assets/95ab331a-9dfb-4f60-9f36-2495eb4c68d6" />
<img width="370" height="282" alt="Screenshot 2026-10-30 221222" src="https://github.com/user-attachments/assets/1a94ad12-5cb8-4007-8810-015055c43105" /><img width="163" height="280" alt="Screenshot 2026-10-30 221234" src="https://github.com/user-attachments/assets/29fc02fa-977d-45a6-b611-be8939861e79" />

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed
<img width="198" height="280" alt="Screenshot 2026-10-30 221537" src="https://github.com/user-attachments/assets/95ab331a-9dfb-4f60-9f36-2495eb4c68d6" />
<img width="203" height="282" alt="Screenshot 2026-10-30 221247" src="https://github.com/user-attachments/assets/818151af-5a94-4b3e-b126-e4ca6dbc1fc0" /><img width="208" height="281" alt="Screenshot 2026-10-30 221259" src="https://github.com/user-attachments/assets/b9a0f6f8-ec6c-4cfc-93b5-e34a31c36c21" />

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed
<img width="198" height="280" alt="Screenshot 2026-10-30 221537" src="https://github.com/user-attachments/assets/95ab331a-9dfb-4f60-9f36-2495eb4c68d6" />
<img width="202" height="281" alt="Screenshot 2026-10-30 221328" src="https://github.com/user-attachments/assets/911b821c-dfa6-4568-b9d6-914d37608a96" /><img width="202" height="286" alt="Screenshot 2026-10-30 221342" src="https://github.com/user-attachments/assets/e565b408-e623-4057-b139-1bcee1859bc5" /><img width="207" height="287" alt="Screenshot 2026-10-30 221351" src="https://github.com/user-attachments/assets/6ebce399-250e-411d-9249-b570ff61a0fe" />

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  
<img width="198" height="280" alt="Screenshot 2026-10-30 221537" src="https://github.com/user-attachments/assets/c2c6f55f-82e9-42fb-beb3-59179479ef4e" />
<img width="205" height="283" alt="Screenshot 2026-10-30 221406" src="https://github.com/user-attachments/assets/170b8d26-9a2c-48f8-afef-e87d543d2269" /><img width="210" height="282" alt="Screenshot 2026-10-30 221416" src="https://github.com/user-attachments/assets/95d92df3-d99f-4261-a6b9-48ef73c1d498" />

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
