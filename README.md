# EDGE--LINKING-HOUGH-TRANSFORM
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import all the necessary modules for the program.
<br>

### Step2:
Load a image using imread() from cv2 module.
<br>

### Step3:
Convert the image to grayscale.
<br>

### Step4:
Using the Canny operator from cv2, detect the edges of the images.
<br>

### Step5:
Using the houghlinesP(), detect the line co-ordinates for every points in the images. Using for loop, draw the lines on the found co-ordinates. Display the image.
<br>


## Program:

# Read image and convert it to grayscale image
```
import cv2
import numpy as np
image = cv2.imread('whale.jpeg') 
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```



# Find the edges in the image using canny detector and display
```
edges = cv2.Canny(gray, 50, 150, apertureSize=3)
```



# Detect points that form a line using HoughLinesP
```
lines = cv2.HoughLines(edges, 1, np.pi / 180, threshold=100)
```


# Draw lines on the image
```
if lines is not None:
    for rho, theta in lines[:, 0]:
        a = np.cos(theta)
        b = np.sin(theta)
        x0 = a * rho
        y0 = b * rho
        x1 = int(x0 + 1000 * (-b))
        y1 = int(y0 + 1000 * (a))
        x2 = int(x0 - 1000 * (-b))
        y2 = int(y0 - 1000 * (a))
        cv2.line(image, (x1, y1), (x2, y2), (0, 0, 255), 2) 
  ```



# Display the result
```
cv2.imshow('original image', image)
cv2.waitKey(0)
cv2.destroyAllWindows()
cv2.imshow('grayscale', gray)
cv2.waitKey(0)
cv2.destroyAllWindows()
cv2.imshow('edge detection', edge)
cv2.waitKey(0)
cv2.destroyAllWindows()
cv2.imshow('Hough Lines Detection', image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```



## Output

### Input image and grayscale image: 
## input image:
![Screenshot 2023-10-11 112830](https://github.com/JeevaGowtham-S/EDGE--LINKING-HOUGH-TRANSFORM/assets/118042624/0f794112-8f30-49a6-8809-3e8a4dfdd14f)
## grayscale image:
![Screenshot 2023-10-11 112648](https://github.com/JeevaGowtham-S/EDGE--LINKING-HOUGH-TRANSFORM/assets/118042624/1c140b61-1560-4e5c-a824-8f610de3b5ef)

<br>
<br>
<br>
<br>

### Canny Edge detector output:
![Screenshot 2023-10-11 112658](https://github.com/JeevaGowtham-S/EDGE--LINKING-HOUGH-TRANSFORM/assets/118042624/360e057c-3ad6-47cc-b1af-bc4e346a8408)

<br>
<br>
<br>
<br>


### Display the result of Hough transform:
![Screenshot 2023-10-11 112705](https://github.com/JeevaGowtham-S/EDGE--LINKING-HOUGH-TRANSFORM/assets/118042624/265f4a26-143f-4ed9-bf47-491dafc25d3d)

<br>
<br>
<br>
<br>



## Result:
Thus the program is written with python and OpenCV to detect lines using Hough transform. 
