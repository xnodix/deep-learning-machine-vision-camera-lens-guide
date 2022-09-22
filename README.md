# Deep Learning and Machine Vision, Camera and Lens Guide

## Intro

Imagine that you were tasked with designing a machine vision system that will deploy deep learning techniques to capture defects in the manufacturing environment. In addition, for the manufacturing setup, we can imagine printed circuit board assembly (PCBA) fab that needs to capture defects like missing components (resistors, capacitors, etc.), skewed components, flipped components, wrong orientation of the componets, and many more in surface mount technology (SMT) footprint.

## System requirements

Assuming the fab is capable of assemblying the components as small as 0603 (metric), which is equivalent to a rectngular shape with 0.6 x 0.3 mm size, we can take 0.3 mm as being the smallest defect that needs to be captured.
In addition, we can assume the largest PCBA is

<img src="RPi2.jpg">
