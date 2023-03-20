# Image-Acquisition-from-Web-Camera
## Aim:
 
To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video

## Software Used
Anaconda - Python 3.7

## Algorithm
### Step 1:
Import cv2 and capture the video using cv2.VideoCapture(0).
### Step 2:
Write the captured image using cv2.imwrite("pic.jpg",frame).

### Step 3:
Resize the image using cv2.resize(frame, (0,0), fx = 0.5, fy=0.5).

### Step 4:
Display the image until the loop gets over.

### Step 5:
Rotate the image using cv2.rotate(smaller_frame,cv2.cv2.ROTATE_180).

## Program:
``` 
### Developed By: M Parshwanath
### Register No: 212221230073
```
```
## i) Write the frame as JPG file
import cv2
videoCaptureObject = cv2.VideoCapture(0)
while(True):
    ret,frame = videoCaptureObject.read()
    cv2.imwrite("pic.jpg",frame)
    result = False
videoCaptureObject.release()
cv2.destroyAllWindows()

## ii) Display the video
import cv2
vdocam=cv2.VideoCapture(0)
while(True):
    ret,frame=vdocam.read()
    cv2.imshow('myimage',frame)
    if cv2.waitKey(1)==ord('x'):
        break
vdocam.release()
cv2.destroyAllWindows()

## iii) Display the video by resizing the window
import cv2
import numpy as np
cap=cv2.VideoCapture(0)
while True:
    ret,frame=cap.read()
    width=int(cap.get(3))
    height=int(cap.get(4))
    image=np.zeros(frame.shape,np.uint8)
    smaller_frame=cv2.resize(frame,(0,0),fx=0.5,fy=0.5)
    image[:height//2,:width//2]=smaller_frame
    image[height//2:,:width//2]=smaller_frame
    image[:height//2,width//2:]=smaller_frame
    image[height//2:,width//2:]=smaller_frame
    cv2.imshow('myimage',image)
    if cv2.waitKey(1)==ord('q'):
        break
cap.release()
cv2.destroyAllWindows()

## iv) Rotate and display the video
import numpy as np
import cv2
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read()
    width = int(cap.get(3))
    height = int(cap.get(4))
    
    image = np.zeros(frame.shape, np.uint8)
    smaller_frame = cv2.resize(frame, (0,0), fx = 0.5, fy=0.5)
    image[:height//2, :width//2] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[height//2:,: width//2] = smaller_frame
    image[:height//2, width//2:] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[height//2:, width//2:] = smaller_frame

    cv2.imshow('frame', image)
    if cv2.waitKey(1) == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```

## Output

### i) Write the frame as JPG image
![img](https://user-images.githubusercontent.com/95388047/226411058-9e47ac4f-b2ef-484f-8744-d731522dc700.png)
### ii) Display the video
![img1](https://user-images.githubusercontent.com/95388047/226411497-f98b4810-0fce-4928-bf33-c32cfefc3a41.png)
### iii) Display the video by resizing the window
![img2](https://user-images.githubusercontent.com/95388047/226411567-fbb6d676-db6c-4019-8b25-8d326af6e882.png)
### iv) Rotate and display the video
![img3](https://user-images.githubusercontent.com/95388047/226411623-579e9659-dcdc-4f57-89f2-022475340423.png)

## Result:
Thus the image is accessed from webcamera and displayed using openCV.
