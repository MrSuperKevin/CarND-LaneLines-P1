# **Report** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:

* Make a pipeline that finds lane lines on the road

* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./report/1.png "Grayscale"
[image2]: ./report/2.png "Canny Edge Detection"
[image3]: ./report/3.png "Masked Lines"
[image4]: ./report/4.png "Result"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

* First, I converted the images to grayscale
* Then I performed Gaussian Blur operation on the grayscaled image following canny edge detection. 
* For the edge image I got from the last step, I perform Hough Transform to get the lines inside.
* Next I filter out the line candidates that is not between 30° and 60° to get possible lane lines.
* Last, I computed the median slope and bias out of the possible lane lines detected from the previous step and draw them on a mask and finally overlay the mask with lines and the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking the median of the detected lines.

There are some of the image samples during the process pipeline showing below.

![alt text][image1]

![alt text][image2]

![alt text][image3]

![alt text][image4]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the image includes a turn. Then the hough line detection method may meet a detection problem. 

Another shortcoming could be the continuity of the line. From the video we can find that the line detected is not very steady and I think this line detecting method cannot possibly be applied to reality for its poor detection ability.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use the information from the previous frame if we are dealing with a short video.
