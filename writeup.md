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


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
