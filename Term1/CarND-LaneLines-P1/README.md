# **Finding Lane Lines on the Road** 

--
The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./test_results/solidWhiteCurve_processed.jpg "Processed"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I used the quiz as example for the pipeline. The base workflow is same as the
quiz.  It consists of following steps:

1. Convert the image to Grayscale
2. Apply Gaussian Blur
3. Apply Canny Edge detection
4. Define Region of Interest
5. Apply Hough Transform to generate required lines

During hough transform, draw_lines() functions is called to draw required
lines on the image.

Following assumption were made to modify this function:
1. The image size is static hence its height and width can be used in
calculating start and end points for the line.
2. Static polygon vertices were chosen. This is also a drawback for the
function which needs improvement.
3. Static slope threshold was deduced by multiple trail and error.
4. Values from quiz were used for hough transform function.

The basic workflow is as follows:
1. Use basic line equation Y= Ax + B as the base and calculate slopes
and coffeciants.
2. Use static slope threshold value to determine position of the points.
of line.
3. use polyfit and poly1d functions to calculate intercept and Y values



### 2. Identify potential shortcomings with your current pipeline

- Algorithm seems to barf on curves or near white vehicles.
- It also doesn't seem to work at all snow is present on road. I tried it
on my personal dash cam video and it fails miserably :-(



### 3. Suggest possible improvements to your pipeline

I see following areas for improvement in this implementation
1. There must be some better way to determine the vertices of polygon.
Need clear understanding and more research.
2. From Quiz excersices it was clear that hough transform was good enough
to give us required lines. I think there must be a way to replace draw_lines()
function all together. Need more research.
3. Need better color filtering. In some pictures this program is not
accurately filtering yellow lines. It also doesn't work as expected where
white lines are not prominent or shadowed due to environment.

