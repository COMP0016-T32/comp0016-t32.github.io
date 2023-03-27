---
title: Research
layout: page
description: Research
---

# Virtual Dance Mat

The initial idea of this project was from the interface of a music video game, Dance Dance Revolution (DDR).

![](https://m.media-amazon.com/images/W/IMAGERENDERING_521856-T2/images/I/51HNfrS+c8L._AC_.jpg)

*Source: [Dance Dance Revolution Regular Dance Pad for Sony Playstation2 PS/PS2 : Amazon.co.uk: PC & Video Games](https://www.amazon.co.uk/Dance-Revolution-Regular-Sony-Playstation2/dp/B000GF7KAW)*

The way to play DDR is usually moving two legs to put them in the right button as well as with the right timing. Since we cannot use physical sensors, we needed to introduce another method and we decided to make a system that detects the different kinds of leg motions (gestures). For 4 arrow buttons in the dance mat above, we set the following leg gestures: 1. putting right leg to right while the left leg stands corresponds to the right arrow 2. the left arrow is triggered in the opposite to the right arrow action 3. for the up arrow, put right leg front while the left leg stands or placed behind a bit, so the shape of the legs looks like scissors 4. for the down arrow, pose the opposite way to the one for the up arrow. Standing straight will be recognised as doing nothing.

## Pose Estimation

Diving into the technical view, in order to achieve our decision, we needed to find a way to detect the leg gestures. Fortunately, one of the famous Computer Vision (CV) applications is pose estimation [1] and it was clear that we need to study. (3D) pose estimation is a technique used to predict human figures through images or videos [2]. During this period, we also investigated the original source code of the MotionInput project and found that it used MediaPipe (Pose estimation library) [3] to detech the face and hand gestures by calculating the distance between the principal body parts of the gestures. Elaborating in more detail, if the distance exceeds a certain threshold, the system determines the corresponding gesture. For instance, if a user poses V sign, it calculates the distances between pairs of coordinates from the two fingers and judges the pose as V sign if the results are above the thresholds.

This was our first idea to implement the leg gestures. However, there was a tiny or big, depending on how you set the objectives, issue with using MediaPipe as a pose estimation library. The function we were about to use was the pose module in MediaPipe, but it requires a face on the screen because the face works as a pivot point of capturing the body. In other words, this will be one of the biggest disadvantages of our project. After noticing this, we decided to look for other alternatives.

## Alternative Pose Estimation Libraries

There is no direct way to detect gestures unless you train a model with the gestures you want to detect. We discovered in two tracks: 1. Train a model with the gestures we want to detect 2. Use a library that can detect the lower body only.
[TODO: FINISH this part]

## Comparison

Advantages using MediaPipe
* Can keep the consistency with the other existing modules that utilise MediaPipe’s solution modules (hand module, for example)
* Model is already implemented, and we can use landmarks provided by MediaPipe to determine gestures.
* Actively used in MotionInput already

Disadvantages using MediaPipe
* Impossible to capture lower body only
* How Dancemat works in DDR
* How do the existing other modules in MI work? (Investigation)
* How to implement it (idea upcoming)
* List up some usable libraries
  * Comparison in several perspectives
* How to use MotionInput

## Final decision



# Hand Jitter Correction
After some research, it has been found that there are various object tracking smoothing methods available for use, depending on the type of system and the nature of the noise present. Some of the commonly used tracking methods include:

* Kalman filtering, suitable for systems with Gaussian noise (which is suitable for our case)
* Particle filtering, which can handle non-linear and non-Gaussian noise
* Laplacian smoothing is a technique used in image processing to reduce noise and smooth out edges by replacing the colour of each pixel with the average colour of its surrounding pixels.

Each of these methods has its strengths and weaknesses, and the choice of method will depend on the specific requirements of the object being tracked. In our case for hand jitter correction, we have chosen to implement Laplacian smoothing and Gaussian filter.
After some research, it has been found that there are various object tracking smoothing methods available for use, depending on the type of system and the nature of the noise present. Some of the commonly used tracking methods include:

## Laplacian Smoothing

Laplacian smoothing [2, 3] is a method used to make guesses or predictions when there isn't a lot of information available, and it helps to make the guesses more accurate.

Laplacian smoothing, also known as add-k smoothing or additive smoothing, is a technique used in probability theory and statistics to smooth categorical data by adding a small value (\\(k\\)) to the frequency of each category.

This technique is useful in cases where there are categories in the data with zero frequencies or very low frequencies, which can result in problems when calculating probabilities or making predictions. By adding a small constant value to the frequency of each category, Laplacian smoothing helps to avoid these problems and produce more accurate results.

The formula for Laplacian smoothing is:

$$ P(x)=\frac{count(x) + k}{N + k \times |V|} $$

where:

\\(P(x)\\) is the smoothed probability of the category \\(x\\)

\\(count(x)\\) is the number of times x appears in the data

\\(N\\) is the total number of observations in the data

\\( \| V \| \\) is the size of the vocabulary (i.e., the number of distinct categories)

\\(k\\) is the smoothing parameter, usually set to 1

Laplacian smoothing is a simple and effective technique, but it can also have some limitations. For example, it assumes that all categories are equally likely a priori, which may not be true in some cases. Additionally, the choice of the smoothing parameter \\(k\\) can have a significant impact on the results, and it may need to be tuned for each specific problem or dataset.

![](../images/research_2_1.png) [1]

**In our case, how to smooth a tracking curve?**
![](../images/research_2_2.png)

## Gaussian Filter (Kalman filter)

Gaussian filter can be used in motion tracking to smooth out noisy position measurements and improve the accuracy of object tracking.

Gaussian filter is a type of linear filter that convolves the input data with a Gaussian function, which is a bell-shaped curve that can effectively remove high-frequency noise while preserving the low-frequency components of the signal.

In motion tracking, Gaussian filter can be applied to the position measurements of an object to remove high-frequency noise, such as random variations and sensor noise. The filtered position measurements can then be used to compute the object's velocity and acceleration, which can provide useful information for predicting the object's future position and tracking its motion over time.

One common approach is to use a Kalman filter, which combines the Gaussian filter with a mathematical model of the object's motion to estimate its position and velocity. The Kalman filter uses the filtered position measurements to update its estimate of the object's state and predict its future position, based on the object's previous position and velocity.

Overall, Gaussian filter can be a powerful tool for motion tracking, as it can effectively remove high-frequency noise and improve the accuracy of position measurements, which is essential for reliable and robust tracking of moving objects.

![](../images/research_2_3.png)

**Kalman filter trajectory estimation**: The measurement - detection noise is set to a relatively high value, but the Kalman filter successfully predicts and corrects object trajectory. [4]

# References

**Virtual Dance Mat Reference**

**Hand Jitter Reference**

[1] N. Xi, Y. Sun, L. Xiao, and G. Mei, "Designing Parallel Adaptive Laplacian Smoothing for Improving Tetrahedral Mesh Quality on the GPU," *Applied Sciences*, vol. 11, no. 12, p. 5543, Jun. 2021, doi: 10.3390/app11125543.

[2] M. Desbrun, M. Meyer, P. Schröder, and A. H. Barr, "Implicit fairing of irregular meshes using diffusion and curvature flow," In *Proceedings of the 26th annual conference on Computer graphics and interactive techniques (SIGGRAPH '99)*, pp. 317–324, Jul 1999.

[3] T. Zhou, H. Bhaskar, F. Liu, J. Yang, et al., "Graph regularized and locality-constrained coding for robust visual tracking," *IEEE Trans. Circuits Syst. Video Technol.*, vol. 27, no. 10, pp. 2153–2164, Oct. 2017.

[4] D. Juric, "Object Tracking: Kalman Filter with Ease," *codeproject.com*, fig. 1, Jan. 15, 2015. [Online]. Available: https://www.codeproject.com/Articles/865935/Object-Tracking-Kalman-Filter-with-Ease. [Accessed Mar. 24, 2023].
