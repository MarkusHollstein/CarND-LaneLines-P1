# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used Gaussian Blur in order to get rid of noise. 
The next step was to use canny edge detection to detect edges within the picture. After that I defined the region to be taken into
consideration for the lane line detection. Finally I used the cv2.HoughLinesP function to filter out the relevant lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by for every line calculating the slope and then dividing into two groups, the first with positive slope and the second with negative slope (I added thresholds in order to ignore horizontal lines), corresponding to the left and right line. For each group I calculated the average slope and the corresponding average c (in the equation y = mx+c). Using these I calculated the starting and end points of the lines to be drawn and printed the lines.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when you drive at night and the lines are not detected well anymore or lights (streetlights, lights of other cars, lights of your own car) influence the edges that are detected.

Another shortcoming could be what happens when you shift the lanes. There would probably be a great confusion during that process.

Besides changes of light and street colours have great influence of the result as in the challenge.

It is not optimal for curves because the line can not exactly represent a curvy lane line.

The result is not yet completely stable. It occasionally jumps.

Other cars are not taken into consideration yet and would probably spoil everything.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to make the draw_lines function more robust by using something else than the average which can be influenced a lot by noise lines. Somehow the lines that do not correspond to the lane line must be filtered better or ignored.

Another potential improvement could be to allow the drawn line to be something different from a straight line in order to better deal with curves.

Probably by tuning parameters the current pipline can still be improved.