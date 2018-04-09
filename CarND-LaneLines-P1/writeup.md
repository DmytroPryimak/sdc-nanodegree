# **Finding Lane Lines on the Road** 

---


The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidYellowLeft.jpg "Solid Yellow Left Annotated"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a gaussian_blur to the image. On top of the blurred image I applied canny transformation. After this step I defined and applied masking of the region of interest on the image. And the last step of a pipeline is applying a Hough transformation, calculating coordinates of the lines and drawing them on top of the image.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating all the points and slopes which belong to right vs left line. Then I extrapolated coordinates for a final lines by finding the means of right/left points and slopes. Also, to make drawing lines in video smoother I took means of coordinates across few frames.

Following is the example of an annotated image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road has a big curve or a sharp turn. As the pipeline is drawing only straight lines, it will produce very imprecise results for such roads. 

Another shortcoming could be when the picture has poor quality or the light in the scene is imbalanced. It can cause very distorted or incorrect drawings.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to reconsider drawing of the straight lines in favor of some more complex curve-like lines.

Another potential improvement could be to preprocess/normalize the image before searching for lines. To make the picture more balanced from the contrasts perspective and try to compensate for possible quality issues.
