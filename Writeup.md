# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"
[image2]: ./test_images_output/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"
[image3]: ./test_images_output/solidYellowCurve2.jpg "solidYellowCurve2"


---

### Reflection


My pipeline consisted of 5 steps. First, I converted the images to grayscale and then I blurred the image using gaussian blur. Afterwards, using canny edge detection algorithm and polygon mask, I identified possible lane edges within area of interest. From this set, using Hough transform, I received a set of detected lines. Not of them represented desired road lines, therefore I filtered out unwanted ones by checking line steepness and its position on the image. 

Initial parameters were taken from the excercises done along the classes, further tuned by experimenting in order to get an intuition how to do it correctly and to get the right results on the image.

In order to draw a single line on the left and right lanes, I gathered all the points corresponding to the lines on one side and fitted a single line using cv2.fitLine, drawing it next between the edges of the region of the interest.

Here are the sample of the pipeline results:

![alt text][image1]
![alt text][image2]
![alt text][image3]


Among identified shortcomings I can definitely mention that the pipeline didn't handle well the challenge video. Apparently the set of parameters I ended up with works only in the very specific conditions present in the sample images and two sample videos. The pipeline seems to be very sensitive to situation when the contrast between lanes and the road is significantly lesser than in sample inputs.

First possible improvement that comes to my mind is to introduce automatic adjustment of some parameters. Perhaps setting the parameters basing on image histogram would be a good path to follow. Additionally better control over false-positive lines would be helpful in order to achieve better lane spatial stability.  

