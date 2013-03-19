# Multiple-camera System Calibration Toolbox for Matlab

This is a toolbox for calibrating multiple-camera systems. The requirement of this toolbox is that two neighbor cameras in your system should be able to see some part of a calibration board at the same time. In general if the angle between the orientations of two neighbor cameras is no more than 90&deg;, this toolbox can work well for your system. 

The toolbox is related to the paper: 

A Multiple-Camera System Calibration Toolbox Using A Feature Descriptor-Based Calibration Pattern, submitted to IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2013. 

This toolbox also exploits some util codes from [Bouguet's calibration toolbox](http://www.vision.caltech.edu/bouguetj/calib_doc/)

---
## Contents

* System requirements
* Quick start
* APIs descriptions
* FAQs

---
## System requirements

The toolbox requires Matlab 2012b or higher version and can be used on Windows, Unix and Linux systems. 

---
## Quick start

### Get your calibration pattern and take images

The toolbox detect SURF features as correspondences for calibration. You can generate a random pattern which is full of SURF features by using this provided Matlab function: 

    pattern = generatePattern(N, M); 

where `N` and `M` are the height and width of the pattern in pixels. 

After printing the pattern and pasting it on a flat board, you can take images of the pattern by your camera system. Your camera system should be well synchronized. Next move the pattern in front of each pair of neighbor cameras and take synchronized images. Make sure that each time both of neighbor cameras can see a sufficient large part of the pattern. For better calibration result, it is also recommended to take some images with the pattern in front of each one camera so that we have images with pattern covering every region of the camera view. 

Images should be named in the form of `camera_index-time_stamp.extension`, e.g. `1-1234.png` or `3-2983.bmp`. The camera index is a 1-based integer and the time stamp is a positive integer. 

### Calibrate your system

Run the `main` script to launch a simple command-line interface for the calibration. Follow each step of the interface. 

1. Select the pattern image file you are using. 

2. Resize the pattern if needed. If you use a large calibration pattern with very high resolution but the camera resolution is much lower, it is better to input a resized smaller pattern into the interface image. This can enhance the feature detection and matching performance. The input scale should be less or equal to 1. 

3. Input number of the cameras. 

4. Select camera models. You can select pinhole model for normal camera, or catadioptric model for catadioptric, fisheye or wide-angle cameras. 

5. Load images. Images should be named in the form of `camera_index-time_stamp.extension`. You can use `Shift` or `Ctrl` keys for multiple selection in the file selection dialog. 

6. Calibration will then automatically launch. 

### An example

This is an example of calibrating a 5-camera rig. [Download the images here]() and follow the following steps: 

Run the calibration interface by calling `main` in Matlab. You will see: 

>     >> main
    ----------------------------------------------------------------------
    Multiple-Camera Calibration Toolbox
    ----------------------------------------------------------------------
    ### Load Pattern
    Input the path of the pattern

Select the pattern image `pattern.png` in the file selection dialog. You will see somthing like this: 

>     /home/li/Workspace/calibration-toolbox/image/pattern.png successfully loaded
    ### Resize Pattern
    Do you need to resize the pattern?
    If the pattern resolution is very high, 
    suitable shrinking can help speed up and enhance the feature detection. 
    Input the scale ([] = no resize): 

Since `pattern.png` has very high resolution, input `0.5` to resize it. Next you will see:

>     Resized to 50%
    ----------------------------------------------------------------------
    ### Camera Numbers
    Input the number of cameras in the system: 

Input `5` since we have 5 cameras in the system. 

>     ### Camera Type
    Use pinhole (1) or catadioptric (2) model for Camera #1 (1/2)? 

Select `2` since this data is from wide angle cameras. 

>     Use the same model for the rest of the cameras (Y/N, []=Y)? 

Press `ENTER` to use the same model for the rest 4 cameras. 

>     ----------------------------------------------------------------------
    ### Load Images
    ### Select images all together (should be named in form "cameraIndex-timeStamp")

Multi-select all images in the file dialog. Then images will be automatically loaded. 






---
## APIs descriptions

Coming soon. 