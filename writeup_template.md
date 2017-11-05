# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report



---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 

1)First I need to grayscale the image to make it easier to process
2)Then i use gaussian_blur function with kernal size 13 to blur the image. But I find that the kernal size won't affect too much for the results.
3)Next I use canny functions to detect the edges of image with threshold as 50 and 150
4)And then I use region_of_interest function to mask out the are i am not interested in by mask it with an polygon shape
5)And next I use hough_lines function to detect the lines based on the edge image in step 4, i tried parameter with many many times and finally it is rho = 2 , threshold = 50, min_line_length = 5,  max_line_gap = 30
6)Lastly, with weighted_img function i draw the red lines in original image and make it transparent


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by differentiate the left lines and right lines by line slope and get the mean of left lines and right lines to calculate a final solid line. 




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are noises in the road espeially wrong lines were detected and also the lines are almose parallel with the real road lane, then it will be very hard to eliminate these noises. 

Another shortcoming could be the are of interest function is not quite generic and could not apply to different sized images.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to find a algorithm by calculating the distance of left lines and right lines and remove the lines which are far away from most other lines. 

Another potential improvement could be to make the are of interest function become generic so that it will adapt to different camera angle and different image size. This may be done intelligently by detect the longest lines detected.