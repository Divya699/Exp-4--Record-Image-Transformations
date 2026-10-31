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

### **Name:**  DIVYA PRIYA S

### Register No: 212225240037

###  Step 1: Load the image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r'C:\Users\acer\Downloads\photo 2.jpeg')

```

###    Display the original image
```
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))

plt.title("Original Image")

plt.axis('off') 
```


###  Step 2: Image Translation
```
tx, ty = 100, 50

M_translation = np.float32([[1, 0, tx], [0, 1, ty]])
```

#### [1, 0, tx] - Horizontal shift by tx

#### [0, 1, ty] - Vertical shift by ty
```
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))

plt.title("Translated Image")

plt.axis('off')
```

### Step 3: Image Scaling
```

image = cv2.imread(r'C:\Users\acer\Downloads\photo 2.jpeg')  # Load the image from file

fx, fy = 5.0, 2.0
```

#### Scaling factors (1.5x scaling for both width and height)
```
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
```
#### resize: Resize the image by scaling factors fx, fy
#### INTER_LINEAR: Uses bilinear interpolation for resizing
```
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))

plt.title("Scaled Image")

plt.axis('off')
```

### Step 4: Image Shearing
```
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])
```
### The matrix shears the image by a factor of 0.5 in both x and y directions
### [1, 0.5, 0] - Shear along the x-axis (horizontal)
### [0.5, 1, 0] - Shear along the y-axis (vertical)
```
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))

plt.title("Sheared Image")

plt.axis('off')
```
### Step 5: Image Reflection
```
reflected_image = cv2.flip(image, 2)

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  
plt.title("Reflected Image")  
plt.axis('off')
```
### Step 6: Image Rotation
```
(height, width) = image.shape[:2]

angle = 45

center = (width // 2, height // 2)

M_rotation = cv2.getRotationMatrix2D(center, angle, 1)

rotated_image = cv2.warpAffine(image, M_rotation, (width, height))

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))

plt.title("Rotated Image")

plt.axis('off')

```
### Step 7: Image Cropping
```
x, y, w, h = 100, 100, 200, 150

# Define the top-left corner (x, y) and the width (w) and height (h) of the crop

# Cropping the image from coordinates (x, y) to (x+w, y+h)

cropped_image = image[y:y+h, x:x+w]

# The crop is performed by slicing the image array in the y and x directions

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))

# Display the cropped image

plt.title("Cropped Image")

plt.axis('off')
```
---

##  Output

### Original Image

<img width="685" height="531" alt="image" src="https://github.com/user-attachments/assets/4776c190-3aa9-429c-926d-0203081dd7e6" />


### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed
<img width="698" height="550" alt="image" src="https://github.com/user-attachments/assets/02b983c1-7fd4-43a8-acca-ab5c92b780e5" />

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed
<img width="719" height="532" alt="image" src="https://github.com/user-attachments/assets/0e8e7949-9e07-43dd-ae46-08e0846e59df" />

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  
<img width="676" height="539" alt="image" src="https://github.com/user-attachments/assets/4e2196bd-5c13-4b62-9568-1a12df15517c" />

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  
<img width="681" height="512" alt="image" src="https://github.com/user-attachments/assets/a961f748-a80f-456b-824c-820487be5de7" />

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed
  
<img width="679" height="559" alt="image" src="https://github.com/user-attachments/assets/d5ce6266-7f78-4f7a-8ae9-8b463dbe5b4d" />

### Image Cropping

<img width="674" height="552" alt="image" src="https://github.com/user-attachments/assets/4639251c-d899-42b8-943e-4b06ab6e7196" />

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
