## Line Detection in Image Mosaics using the Hough Transformation

**Project description:** 

The intent of this program is to incorporate both surveyed points and drone flight imagery to automatically detect and create lines. This is achieved by a program that reads in and analyzes the drone ortho image.
An image of a portion of a drone flight ortho image is shown below, with blue points overlayed representing surveyed points collected in the field.

<src img="images/OrthoImagePoints.png?raw=True"/>

Using an image blur with canny line detection, the image is turned into a raster and put through a Hough Lines transform using cv2.HoughLinesP(). The returned image is shown below.

<src img="images/OrthoImageCanny.png?raw=True"/>

The hough-space undergoes a series of comparisons where if a continuous line formed by two surveyed points crosses a series of continuous pixels formed from the Hough Transform, a new line is created. This results in many new lines used to test if any two points lie on this line and are the closest possible points to each other, then a new line segment is formed. Although this allows for lines going "through" obscurants like trees and cars, it can also over produce and create line segments that should not fit one another. A final representation can be seen below.

<src img="images/OrthoImageLines.png?raw=True"/>
