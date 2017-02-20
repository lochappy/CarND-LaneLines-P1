#**Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[grayImg]: ./OutputImages/gray_img.png "Grayscale"
[smoothedGrayImg]: ./OutputImages/smooth_img.png "Smoothed Gray Image"
[cannyImg]: ./OutputImages/canny_img.png "Canny Image"
[maskedCannyImg]: ./OutputImages/masked_canny_img.png "Masked Canny Image"
[laneLineImg]: ./OutputImages/lane_line_image.png "Lane Line Image"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

There are totally 5 steps in my pipeline as following:

1. Converting the images to grayscale: ![alt text][grayImg]

2. Smoothing the images using Gaussian Filter: ![alt text][smoothedGrayImg]

3. Detecting the edges in images by Canny Algorithm: ![alt text][cannyImg]

4. Selecting the edges within the ROI: ![alt text][maskedCannyImg]

5. Finding the Hough lines: ![alt text][laneLineImg]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a new parameter called `filter_left_and_right_lane_lines`. This `filter_left_and_right_lane_lines` takes all of the lane line segments (`line_segments`) as its input, splits `line_segments` to the left and the right lane line groups based on their slopes. Then, the median slope and bias of each group will be calculated. At the end, the `filter_left_and_right_lane_lines` returns the unique left and right lane line, which are finally drawed to the image.


###2. Identify potential shortcomings with your current pipeline


The detection lines are quite jittering. We can stablize it by some filters such as Kalmal filter.

The pipeline heavily depends on the hard-coded parameters such as the region of interest, the thresholds of canny function, the parameters of the hough transform, etc. Therefore, it is only able to withstand the image condition up to some level. When the condition changes dramatically, like from the sunlight to night or heavily rain, those parameters must be recalibrated, causing the inconvenience. 


###3. Suggest possible improvements to your pipeline

The other color spaces can be used to extract the edge image instead of using grayscale, for example, HSV, LUV, etc.

Histogram equalization can be applied to stablize the contrast of the image, making the edge detection robust to illumination change. 

Motion model, such as Kalmal Filter, also can be applied to the slopes and biases of the detected lane lines in order to keep track of them in case there is no detection found.
