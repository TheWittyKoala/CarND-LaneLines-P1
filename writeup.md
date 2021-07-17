# **Finding Lane Lines on the Road**
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"

---

### Reflection

### 1. Pipeline Description

My pipeline consistes of the 6 following steps :

* Greyscale the image.
* Apply the Gaussian Blur to the greyscaled image.
* Apply the Canny Edge Detection to the resulted image.
* Apply the Region Masking to the previous image.
* Apply the Hough Transformation to the edge detected image.
* Draw the lines on the initial image using basic linear regression to determine the params of the extrapolated resulting line.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by including a slope-based filter, firstly by creating lists of coordinates to calculate the slopes of each segment to :
* Get rid of low slope segments, which means horizontal lines.
* Sort each segment in the to the right line : positive slopes -> right line, and a negative ones -> left line.

After that, I applied a simple linear regression on each line using np.polyfit(XXs, YYs, 1) in order to extrapolate the points along the lane to form solide side lines.

Here's one of the resulting images: 

![alt text][image1]


### 2. Potential shortcomings with my current pipeline


One potential shortcoming would be what would happen when when the meteorological conditions change, such as light/shades or weather (rainy days).

Another shortcoming would be what would happen if the state of the road was catastrophic (holes, trees or rural roads)


### 3. Possible improvements to my pipeline

A possible improvement would be to work more on the smoothing of the lines, especialy in the video processing.

Another potential improvement could be to use some "advanced" technics to predict lines incurving.
