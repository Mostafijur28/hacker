
---
layout: default
---

## Project

This project is all about counting the number of objects present in an image. We count the number of edges that are presner inside the image using Canny Algorithm.

Tools utilised : 

OpenCV, Matplotlib, numpy

```python

#Implementation
  
import cv2
import numpy as np
import matplotlib.pyplot as plt
  
image = cv2.imread('assets/img/coins.png')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
  
blur = cv2.GaussianBlur(gray, (11, 11), 0)
canny = cv2.Canny(blur, 30, 150, 3)
dilated = cv2.dilate(canny, (1, 1), iterations=0)
  
(cnt, hierarchy) = cv2.findContours(
    dilated.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
cv2.drawContours(rgb, cnt, -1, (0, 255, 0), 2)
  
  
print("coins in the image : ", len(cnt))
