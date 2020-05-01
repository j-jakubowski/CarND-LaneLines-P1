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


My pipeline consisted of 5 steps. First, I converted the images to grayscale and then I blurred the image using gaussian blur. Afterwards, using canny edge detection algorithm and polygon mask, I identified possible lane edges within area of interest. From this set, using Hough transform, I received a set of detected lines. Not of them represented desired road lines, therefore I filtered out unwanted ones by checking line steepness and its position on the image. 

In order to draw a single line on the left and right lanes, I gathered all the points corresponding to the lines on one side and fitted a single line using cv2.fitLine, drawing it next between the edges of the region of the interest.

Here are the sample of the pipeline results:

![alt text][image1]


One identified shortcomming



First possible improvement that comes to my mind is to somehow automate adjusting some of the parameters. Clearly the pipeline doesn't work really well on the 'challange' video, especially where the contrast between the tarmac and the lane is very low. Perhaps setting the parameters basing on image histogram would do the job? 

