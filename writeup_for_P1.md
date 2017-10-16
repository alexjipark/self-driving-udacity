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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then secondly I applied gaussian blur to the images. 
At thrid, Canny edge detection was to extract edges of images, then the images were transformed into Hough space in
order to detect lane lines. Finally I drew lane lines according to the calculation for extrapolating several lane lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
figuring out the longest lines for each left and right side among detected lines and 
applying slope and intercept of the longest lines to one line for each sides.

If you'd like to include images to show how the pipeline works, here is how to include an image: 


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there's not much difference between the length of most detected lines.
If that's the case, the longest line would be not representative for lanes, which would mislead the result.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to average slope and intercept of majority of detected lanes which has similarity
in the values within certain ranges. (+- 5%)

Another potential improvement could be to detect differences between consecutive images in video 
and not to apply any changes to current image if there's no 'big' difference between them.
(It might stabilizes two single lines for each side.)
