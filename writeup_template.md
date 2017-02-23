#**Finding Lane Lines on the Road**

[//]: # (Image References)

[image1]: ./sample/gray.jpg "gray_sample"
[image2]: ./sample/gaussian_blur.jpg "gaussian_blur_sample"
[image3]: ./sample/canny_transform.jpg "canny_transform_sample"
[image4]: ./sample/mask.jpg "mask_sample"
[image5]: ./sample/hough_transform.jpg "hough_transform_sample"
[image6]: ./sample/combined.jpg "combined_sample"

[image7]: ./test_images/output_whiteCarLaneSwitch.jpg "processed_whiteCarLaneSwitch"
[image8]: ./test_images/output_solidYellowCurve2.jpg "processed_solidYellowCurve2"
[image9]: ./test_images/output_solidYellowLeft.jpg "processed_solidYellowLeft"
[image10]: ./test_images/output_solidWhiteCurve.jpg "processed_solidWhiteCurve"
[image11]: ./test_images/output_solidWhiteRight.jpg "processed_solidWhiteRight"
[image12]: ./test_images/output_solidYellowCurve.jpg "processed_solidYellowCurve"

[image13]: ./test_images/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"
[image14]: ./test_images/solidYellowCurve2.jpg "solidYellowCurve2"
[image15]: ./test_images/solidYellowLeft.jpg "solidYellowLeft"
[image16]: ./test_images/solidWhiteCurve.jpg "solidWhiteCurve"
[image17]: ./test_images/solidWhiteRight.jpg "solidWhiteRight"
[image18]: ./test_images/solidYellowCurve.jpg "solidYellowCurve"


##Pipeline description

My pipeline consists of 6 steps. First, I convert input image to grayscale

![alt text][image1]


Then I apply gaussian blur to image.

![alt text][image2]


The resulting image is then processed with canny function.

![alt text][image3]


The image is further processed with region_of_interest function.

![alt text][image4]


Hough transform  is then applied on image

![alt text][image5]


Finally, the output image from the hough transform and the original image are combined using weighted_img function

![alt text][image6]





In order to draw a single line on the left and right lanes, I modified the draw_lines() function by storing x and y coordinates of lines according to their slopes.Theses values are then used to calculate slopes and centers of the left and right lane which in turn is used to calculate the coordinates to draw the left and right lane lines.








Below are the original and processed images from test_images folder

![alt text][image13] ![alt text][image7]
![alt text][image14] ![alt text][image8]
![alt text][image15] ![alt text][image9]
![alt text][image16] ![alt text][image10]
![alt text][image17] ![alt text][image11]
![alt text][image18] ![alt text][image12]


##shortcomings

The lines created to trace out road lanes are constrained within a tight slope range. So this pipeline will not work well with road lanes that are angled at a different slope outside the defined slope constraint.

This pipeline will perform well when lanes lines are brightly colored (white or yellow) but will not perform well when the lane lines are dull or in poor lighting conditions




##improvements

Modify pipeline to accommodate a wide range of slopes for lane lines.

Modify pipeline to perform well regardless of lane lines color brightness or lighting condition.
