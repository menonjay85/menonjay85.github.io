---
title: "ROI-bounded Visual Odometry"
author_profile: true
toc: true
key: 1
excerpt: "Computer Vision, OpenCV, RealSense Camera"
header:
  teaser: /assets/images/visual-odom1.gif
classes: wide
---

## Simulation Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/W2t_6aUduIM"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Overview

This project aims to develop a monocular visual odometry implementation that estimates a moving camera's pose while reducing run-time, making it suitable for embedded systems and personal devices with limited computational resources.

Traditional monocular visual odometry involves matching local features on successive frames and calculating the Essential Matrix and 3D point triangulation. However, this process is often computationally expensive, especially when using feature-rich algorithms like SIFT. Alternatively, less resource-intensive features like ORB are challenging to match between frames and lead to lower visual odometry performance.

SIFT is more accurate but notably more resource-intensive than ORB. For instance, generating SIFT features for a 600 by 1200 image takes around 0.40s on a 12-core Intel i5 PC, while ORB requires only 0.07s per image. Therefore, using SIFT in compact embedded systems and personal devices with AR/VR capabilities can severely affect real-time performance, which is critical for these applications.

This project aims to leverage the accuracy of feature-rich algorithms like SIFT while minimizing computational resources. The approach primarily focuses on regions of the image that are likely to yield high-quality features, thereby reducing the need for extensive computations across the entire image.

## Baseline Implementation

### Local Feature Extraction
In this project, I utilized OpenCV's SIFT_create(), ORB_create(), and detectAndCompute() functions to extract 2D coordinates and descriptors of local features. SIFT, for instance, identifies local maxima and minima across scales and generates a descriptor vector for each keypoint.

### Feature Matching
I used the K-nearest neighbor method to match keypoints in successive frames, employing a ratio test to exclude false matches. Matches with a ratio below 0.5 were typically included.

### Pose Estimation
To determine the camera pose transformation, I calculated the Essential Matrix using camera's intrinsic parameters and feature points. OpenCV's findEssentialMat function aided in this process. From the Essential Matrix, I derived two potential rotations and translations, creating four candidates for projection matrices. By triangulating 3D points from matched 2D points and assessing the quantity of points in front of the camera and the relative scale factor, I selected the optimal candidate for the camera motion. The relative scale factor was computed by comparing mean distances between successive feature points in different frames.

## Object-bounded Visual Odometry
One strategy to enhance the run-time of the baseline approach involves initially employing a fast object detection model to identify object bounding boxes, and then extracting features solely within these bounding boxes. This is because objects are likely to harbor features rich in information that can be easily matched if they persist in the subsequent frame. This idea stems from the observation that while running SIFT feature extraction takes an average of 0.40s on my laptop, it only takes about 0.30s to run the cutting-edge object detection model YOLO-NAS (small version).
This method initially employs the object detection model to derive bounding boxes, and then exclusively extracts SIFT features from within these bounding boxes, as opposed to the entire image. The remainder of the visual odometry pipeline is akin to the baseline approach.

## ROI-bounded Visual Odometry
Instead of leveraging object detection models to generate bounding boxes, we can propose regions of interest (ROIs) to extract local features. My methodology of ROI proposal incorporates Canny Edge Detection, contour extraction, bounding box placement around contours, and contour box size filtration.
I initially apply the OpenCV Canny method to discover an edge map of an image. I then employ the OpenCV findContours method to trace and segregate contours present in the edge map. For each contour, I generate the smallest possible bounding box capable of encompassing the entire contour. I then filter these boxes using both a low and high area threshold to eliminate minuscule contours that are likely unbeneficial and large contours that may increase computation.
After acquiring the filtered contour boxes, I extract SIFT features solely from these contour boxes as opposed to the entire image. The remainder of the process mirrors the baseline approach.

### Cascade Processing
To further diminish run-time, we can utilize cascade-style processing. Since ROI extraction is not an exact process and does not require pinpointing the exact locations of all visible contours, we can initially decrease the resolution of the input image for ROI proposal, and then utilize the original image for feature extraction within the proposed ROIs.

### Predictive Pose Estimation
Sometimes, particularly when there are fewer feature point matches, erroneous pose estimations may occur. To mitigate this, I've attempted to calculate a weighted sum of the previous transformation and the new transformation, collectively forming the new transformation. This approach assists in mitigating incorrect estimations by assuming that the camera typically moves in a manner similar to its past.

### IoU Filtering
Another issue that has come to my attention is that some proposed ROI bounding boxes can overlap, which leads to duplicate feature detection and unnecessary computation. To eliminate these redundant bounding boxes, I employ Intersection over Union (IoU) to filter out overlapping bounding boxes. IoU is computed as the ratio between the intersection area of two bounding boxes and the union of these two boxes.

## Deploying in the Real-world
In order to run experiments to assess the proposed methods, I've developed a package for the Robot Operating System (ROS) that reads images from an Intel RealSense D435i, computes odometry paths using the suggested methods, and visualizes the path in RViz, a 3D visualizer for ROS.

## Result & Analysis
In order to evaluate the methods delineated in the previous section, we utilize a 50-frame test sequence from the renowned KITTI dataset. This dataset is extensively used for assessing tasks in mobile robotics and autonomous driving. The accuracy of a visual odometry method is gauged using both the error in translation and rotation. For run-time, we will assess the average time required to process a single frame.

The evaluation of the different visual odometry implementations revealed the object-bounded method underperformed in both path accuracy and run-time compared to the baseline. This was attributed to the substantial overhead of the object detection model and the restrictive nature of object bounding boxes, with performance particularly compromised in scenarios with few or very small objects.

Conversely, the ROI-bounded visual odometry method substantially improved upon the baseline. It achieved similar accuracy but with less than a third of the runtime when using SIFT. A specific configuration of the ROI-bounded method, combining a lower ROI area threshold of 50, a higher threshold of 500, and non-predictive pose estimation, yielded the best outcomes, demonstrating the lowest runtime and error.

Remarkably, even compared to the baseline method employing ORB, the proposed ROI-bounded visual odometry method offered significantly reduced error, with only a slight increase in runtime.

## Future Work
If we could secure the transition model of the camera, or employ additional sensors such as IMU and LiDAR, we might experiment with state estimation techniques such as the Extended Kalman Filter and Particle Filter. These methods facilitate sensor fusion, incorporating complementary information from other sensors to enhance accuracy and robustness.
At present, when identifying the K nearest neighbors to a feature point, we use Euclidean distance. A superior alternative that considers the distribution of the feature points in the next frame involves the use of Mahanalobis distance.
Further improvements to the performance of our visual odometry implementation might be made through the use of a stereo camera in place of a monocular one, implementing bundle adjustment, and incorporating loop closure detection.

## Real-life Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/BRdMaBKmHJc"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>