**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidYellowCurve-with-lines.jpg "White curve"
[image2]: ./test_images/solidWhiteCurve-with-lines.jpg "White curve with lines"
---

### Reflection

### 1. My pipeline

First, I converted the images to grayscale, then I ran guassian blur as well as canny edge detection in order to get edges. I then used the edges and points in the region of interest function to get a mask of the region of interest for my lane. Next I got the hough lines from my new region of interest. I used the hough lines to get points from both the right and left lines. These points were then used in numpy's polyfit method to fit a line to all the points. From there I simply drew that line over the lane image using a weighted image, so that it would be semi-transparent.


Here's a couple of examples with white and yellow lanes. It is however, still visible all the way through.

![alt text][image2]
![alt text][image1]

Note that the lines on the yellow lanes aren't as clear as the lines with white lanes.

### 2. Potential shortcomings with the pipeline

My biggest shortcoming at this point was that yellow lines would often have difficulties registering. Although most of the spastic behavior from my drawn-on lines has been addressed, I still see an occasional twitch in videos. 


### 3. Improvements to the pipeline

The first potential improvement is one I decided to use, instead of using the greyscale image, I took solely the red channel from my image. 

Another potential improvement could be more parameter tuning. This includes everything from canny thresholds to line lengths and gaps. There seems to be a fine *line* between overfitting and having parameters that accept too general of lines. Both potential problems are clearly visible, since the line will jump to objects other than lane lines. I think trying this on a lot more test images could help ensure that none of the parameters are too constricting or too broad.
