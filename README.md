# Deep Learning and Machine Vision, Camera and Lens Guide

## Intro

Imagine that you were tasked with designing a machine vision system that will deploy deep learning techniques to capture defects in the manufacturing environment. Additionally, for the manufacturing setup, we can imagine printed circuit board assembly (PCBA) fab that needs to capture defects like missing components (resistors, capacitors, etc.), skewed components, flipped components, wrong orientation of the componets, and many more in surface mount technology (SMT) footprint.

## System requirements

Assuming the fab is capable of assemblying the components as small as 0603 (metric), which is equivalent to a rectngular shape with 0.6 x 0.3 mm size, we can take 0.3 mm as being the smallest defect that needs to be captured.
In addition, we can assume the largest PCBA is 85 x 56 mm (RPi2) below, and it comes under the field-of-view (FOV) of the camera on a conveyor belt that is 100 mm wide moving at the speed of 100 mm/s. Since the board can be anywhere on the coveyor belt, our system's overall FOV is 100 x 85 mm. That is, 100 mm  for the width of the conveyor, and 85 mm for the RPi2's length.

<img src="RPi2.jpg">

[Image 1 source](https://images.prismic.io/rpf-products/5d56c54b-59a5-4d9c-8c01-6caf6d43772c_pi2%20B%20Top%20Down.jpg?ixlib=gatsbyFP&auto=compress%2Cformat&fit=max&w=600&h=400)

## Camera Resolution

Given the above information, we are now able to calculate the minimum camera resolution needed to capture the smallest defect in the given FOV.
To make these calculations, use [Camera and Lens guide.](https://docs.google.com/spreadsheets/d/1Z2F2R_iJZvdFtYngHKgEF5hhIu-o1xkFQkvjp5klu40/edit?usp=sharing)

<img src="Camera.png">

Based on our calculations, we need a 9.44 MP camera in order to capture 0603 size defective component on a PCBA.

## Camera selection

When we talk about camera resolution, what we really mean is the imaging sensor resolution. There are many camera manufacturers, and only a handful of imaging sensor manufacturers; Sony being among the most popular one.
Here is a short list of popular Sony imaging sensors, and some specs:

|Product|Resolution|Pixels HxV|Pixel size microns|
|:----|:----|:----|:----|
| | | | |
|IMX661-AAMR/AAQR|127 M|13472 x 9568|3.45|
|IMX342LLA/LQA|31.4 M|6480 x 4860|3.45|
|IMX530-AAMJ/AAQJ|24.5 M|5328 x 4608|2.74|
|IMX540-AAMJ/AAQJ|24.5 M|5328 x 4608|2.74|
|IMX531-AAMJ/AAQJ|20.3 M|4512 x 4512|2.74|
|IMX541-AAMJ/AAQJ|20.3 M|4512 x 4512|2.74|
|IMX367LLA/LQA|19.6 M|4432 x 4436|3.45|
|IMX387LLA/LQA|16.8 M|5472 x 3084|3.45|
|IMX532-AAMJ/AAQJ|16.1 M|5328 x 3040|2.74|
|IMX542-AAMJ/AAQJ|16.1 M|5328 x 3040|2.74|
|IMX535-AAMJ/AAQJ|12.4 M|4128 x 3008|2.74|
|IMX545-AAMJ/AAQJ|12.4 M|4128 x 3008|2.74|
|IMX565-AAMJ/AAQJ|12.4 M|4128 x 3008|2.74|
|IMX304LLR/LQR|12.3 M|4112 x 3008|3.45|
|IMX253LLR/LQR|12.3 M|4112 x 3008|3.45|
|IMX267LLR/LQR|8.9 M|4112 x 2176|3.45|
|IMX255LLR/LQR|8.9 M|4112 x 2176|3.45|
|IMX487-AAMJ|8.1 M|2856 x 2848|2.74|
|IMX536-AAMJ/AAQJ|8.1 M|2856 x 2848|2.74|
|IMX546-AAMJ/AAQJ|8.1 M|2856 x 2848|2.74|
|IMX566-AAMJ/AAQJ|8.1 M|2856 x 2848|2.74|
|IMX428LLJ/LQJ|7.1 M|3216 x 2208|4.5|
|IMX420LLJ/LQJ|7.1 M|3216 x 2208|4.5|
|IMX537-AAMJ/AAQJ|5.1 M|2472 x 2064|2.74|
|IMX547-AAMJ/AAQJ|5.1 M|2472 x 2064|2.74|
|IMX548-AAMJ/AAQJ|5.1 M|2472 x 2064|2.74|
|IMX567-AAMJ/AAQJ|5.1 M|2472 x 2064|2.74|
|IMX568-AAMJ/AAQJ|5.1 M|2472 x 2064|2.74|
|IMX250LLR/LQR|5.0 M|2464 x 2056|3.45|
|IMX264LLR/LQR|5.0 M|2464 x 2056|3.45|
|IMX265LLR/LQR|3.1 M|2064 x 1544|3.45|
|IMX252LLR/LQR|3.1 M|2064 x 1544|3.45|
|IMX437LQJ|2.8 M|1944 x 1472|4.5|
|IMX429LLJ/LQJ|2.8 M|1944 x 1472|4.5|
|IMX421LLJ/LQJ|2.8 M|1944 x 1472|4.5|
|IMX392LLR/LQR|2.3 M|1936 x 1216|3.45|
|IMX174LLJ/LQJ|2.3 M|1936 x 1216|5.86|
|IMX302LQJ|2.3 M|1936 x 1216|5.86|
|IMX249LLJ/LQJ|2.3 M|1936 x 1216|5.86|
|IMX430LLJ/LQJ|2.0 M|1632 x 1248|4.5|
|IMX422LLJ/LQJ|2.0 M|1632 x 1248|4.5|
|IMX432LLJ/LQJ|1.7 M|1608 x 1104|9|
|IMX425LLJ/LQJ|1.7 M|1608 x 1104|9|
|IMX296LLR/LQR|1.5 M|1456 x 1088|3.45|
|IMX273LLR/LQR|1.5 M|1456 x 1088|3.45|
|IMX433LLJ/LQJ|0.5 M|816 x 624|9|
|IMX426LLJ/LQJ|0.5 M|816 x 624|9|
|IMX297LLR/LQR|0.4 M|728 x 544|6.9|
|IMX287LLR/LQR|0.4 M|728 x 544|6.9|
|IMX397CLN|0.3 M|656 x 496|3.45|
|IMX250MZR/MYR|5.0 M|2464 x 2056|3.45|
|IMX253MZR/MYR|12.3 M|4112 x 3008|3.45|
|IMX264MZR/MYR|5.0 M|2464 x 2056|3.45|
|IMX411ALR/AQR|151 M|14208 x 10656|3.76|
|IMX461ALR/AQR|102 M|11664 x 8750|3.76|
|IMX455ALK-K|61.1 M|9576 x 6388|3.76|
|IMX492LLJ/LQJ|47.0 M|8336 x 5648|2.315|
|IMX571BLR-J|26.1 M|6252 x 4176|3.76|
|IMX183CLK-J/CQJ-J|20.4 M|5544 x 3694|2.4|
|IMX226CLJ|12.4 M|4072 x 3046|1.85|
|IMX533CLK|9.0 M|3011 x 3011|3.76|
|IMX335LLN|5.1 M|2616 x 1964|2|
|IMX424|7.42M| |2.25|
|IMX490|5.40M| |3|
|IMX390CPV|2.45M| |3|
|IMX390CQV|2.45M| |3|
|IMX290NQV|2.13M| |2.9|
|IMX224|1.27M| |3.75|
|ISX019|1.23M| |2.9|
|ISX016|1.26M| |2.8|

Since we need a sensor of at least 9.44 MP, IMX253LLR/LQR from the above list looks likea good candidate. There are many camera manufacturers that use Sony sensors, and some of the well known ones are TeledyneDalsa, AlliedVision, IDS Imaging, JAI, etc. Some of them might have a camera that incroporates this particular imaging sensor.

## Lens Calculations

Once we know the pixel size of the sensor as well as number of pixels in horizontal and vertical directions, we can calculate most lens parameters using
[Camera and Lens guide.](https://docs.google.com/spreadsheets/d/1Z2F2R_iJZvdFtYngHKgEF5hhIu-o1xkFQkvjp5klu40/edit?usp=sharing).
In our example, it looks like this:



