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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I use the gaussian blur function to reudce detail (noise) in the image, thus keeping the important main features. After that, I use Canny algorithm (built in opencv) to get the edges in the entire figure, and pass it to a ROI (Region Of Interest) area which is indeed a trapezoid shape. After all, conbine the edges (which is already in ROI) and the orgininal edges (which is from Canny) to get the output lane-detected image.

After the model is built, I tune the hyperparameters serveral times to get the model can generated the lines clearly besides the car. After the hyperparameters is tuned, I saved the lane-detected images to the target folder.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by passing a larger value 10 to parameter `thickness` value.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are noises and we detected much more edges than we want.

Another shortcoming could be we cannot ensure the car is always detecting a lane left and a lane at right.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to check the top longest lines, and develop a non-longest supression algorithm (such as non-max supression in Computer Vision); and finally get the two longest lines (dashed-line or solid-line).

Another potential improvement could be to split the pictures to 2 ROIs (one on the left-downside, another on the right-downside) instead of a single ROI, and detect left lane and right lane respectively.
