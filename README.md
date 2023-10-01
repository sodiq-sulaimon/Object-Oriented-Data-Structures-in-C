# Object-Oriented-Data-Structures-in-C
Programming Assigment

This assignment has 2 parts:
## Part 1:
In part one, I created a class called HSLAPixel within the uiuc namespace in the file uiuc/HSLAPixel.h. Each pixel contains four public member variables:
* h, storing the hue of the pixel in degrees between 0 and 360 using a double
* s, storing the saturation of the pixel as a decimal value between 0.0 and 1.0 using a double
* l, storing the luminance of the pixel as a decimal value between 0.0 and 1.0 using a double
* a, storing the alpha channel (blending opacity) as a decimal value between 0.0 and 1.0 using a double

## Part 2:
In the second part of the assignment, I implemented the functions in ImageTransform.cpp: illinify, spotlight, and watermark. The descriptions are as below:

### Function #1: illinify
To illinify an image is to transform the hue of every pixel to Illini Orange (11) or Illini Blue (216). 
The hue of every pixel is set to one or the other of these two hue values, based on whether the pixel's original hue value is closer to Illini Orange or Illini Blue. 

### Function #2: spotlight
To spotlight an image is to create a spotlight pattern centered at a given point (centerX, centerY).
A spotlight adjusts the luminance of a pixel based on the distance between the the pixel and the designated center by decreasing the luminance by 0.5% per 1 pixel unit of Euclidean distance, 
up to an 80% decrease in luminance at most.
For example, a pixel 3 pixels above and 4 pixels to the right of the center is a total of sqrt(3*3 + 4*4)
= sqrt(25) = 5 pixels away and its luminance is decreased by 2.5% (0.975 its original value). 
At a distance over 160 pixels away, the luminance will always be decreased by 80% (0.2x its original value).

### Function #3: watermark
To watermark an image is to lighten a region of it based on the contents of another image that acts as a stencil.
The range of pixel coordinates that exist in both images are considered; for simplicity, the assumption is that the images are positioned with their upper-left corners overlapping at the same coordinates.
For every pixel that exists within the bounds of both base image and stencil, the luminance of the base image is increased by +0.2 (absolute, but not to exceed 1.0) if and only if the luminance of the stencil at the same pixel position is at maximum (1.0).
