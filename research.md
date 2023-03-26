---
title: Research
layout: page
description: Research
---

# Virtual dance mat

The initial idea of this project was from the interface of a music video game, Dance Dance Revolution (DDR).

[TODO: Put DDR image]

(Copyright: [Dance Dance Revolution Regular Dance Pad for Sony Playstation2 PS/PS2 : Amazon.co.uk: PC & Video Games](https://www.amazon.co.uk/Dance-Revolution-Regular-Sony-Playstation2/dp/B000GF7KAW))

The way to play DDR is usually moving two legs to put them in the right button as well as with the right timing. Since we cannot use physical sensors, we need to make a system that detects the different kinds of leg motions (gestures). For 4 arrow buttons in the dance mat above, we decided the following leg gestures: 1. putting right leg to right while the left leg stands corresponds to the right arrow 2. the left arrow is triggered in the opposite to the right arrow action 3. for the up arrow, put right leg front while the left leg stands or placed behind a bit, so the shape of the legs looks like scissors 4. for the down arrow, pose the opposite way to the one for the up arrow. Standing straight will be recognised as doing nothing.

## Pose Estimation

Fortunately, one of the famous Computer Vision (CV) applications is pose estimation and it was clear that we need to study. (3D) pose estimation is a technique used to predict human figures through images or videos. Since one of our requirements was to make the program works with a webcam, we could step forward with an idea of the pose estimation method.

At the same time, we investigated the existing solutions for face and hand gestures in MotionInput. The common methodology was to calculate the distance between the principal parts of the body, in other words, landmarks. If the distance exceeds a certain threshold, the system determines the corresponding gesture. For example, if a user poses V sign, it calculates the distances between pairs of coordinates from the two fingers and judges the pose as V sign if the results are above the thresholds.

## Comparison

Advantages using MediaPipe
*	Can keep the consistency with the other existing modules that utilise MediaPipe’s solution modules (hand module, for example)
*	Model is already implemented, and we can use landmarks provided by MediaPipe to determine gestures.
*	Actively used in MotionInput already

Disadvantages using MediaPipe
*	Impossible to capture lower body only
*	

*	How Dancemat works in DDR
*	How do the existing other modules in MI work? (Investigation)
*	How to implement it (idea upcoming)
*	List up some usable libraries
  *	Comparison in several perspectives
*	How to use MotionInput

[TODO: FINISH this part]

# Hand Jitter Correction
After some research, it has been found that there are various object tracking smoothing methods available for use, depending on the type of system and the nature of the noise present. Some of the commonly used tracking methods include:

• Kalman filtering, suitable for systems with Gaussian noise (which is suitable for our case)
• Particle filtering, which can handle non-linear and non-Gaussian noise
• Laplacian smoothing is a technique used in image processing to reduce noise and smooth out edges by replacing the colour of each pixel with the average colour of its surrounding pixels.

Each of these methods has its strengths and weaknesses, and the choice of method will depend on the specific requirements of the object being tracked. In our case for hand jitter correction, we have chosen to implement Laplacian smoothing and Gaussian filter.
After some research, it has been found that there are various object tracking smoothing methods available for use, depending on the type of system and the nature of the noise present. Some of the commonly used tracking methods include:

## Laplacian Smoothing

Laplacian smoothing is a method used to make guesses or predictions when there isn't a lot of information available, and it helps to make the guesses more accurate.

Laplacian smoothing, also known as add-k smoothing or additive smoothing, is a technique used in probability theory and statistics to smooth categorical data by adding a small value (k) to the frequency of each category.

This technique is useful in cases where there are categories in the data with zero frequencies or very low frequencies, which can result in problems when calculating probabilities or making predictions. By adding a small constant value to the frequency of each category, Laplacian smoothing helps to avoid these problems and produce more accurate results.

The formula for Laplacian smoothing is:

P(x) = (count(x) + k) / (N + k * |V|)

where:

P(x) is the smoothed probability of the category x
count(x) is the number of times x appears in the data
N is the total number of observations in the data
|V| is the size of the vocabulary (i.e., the number of distinct categories)
k is the smoothing parameter, usually set to 1
Laplacian smoothing is a simple and effective technique, but it can also have some limitations. For example, it assumes that all categories are equally likely a priori, which may not be true in some cases. Additionally, the choice of the smoothing parameter k can have a significant impact on the results, and it may need to be tuned for each specific problem or dataset.

[TODO: Put picture1]
(Xi et al. 2021)

**In our case, how to smooth a tracking curve?**
[TODO: Put picture2]

## Gaussian Filter (Kalman filter)

Gaussian filter can be used in motion tracking to smooth out noisy position measurements and improve the accuracy of object tracking.

Gaussian filter is a type of linear filter that convolves the input data with a Gaussian function, which is a bell-shaped curve that can effectively remove high-frequency noise while preserving the low-frequency components of the signal.

In motion tracking, Gaussian filter can be applied to the position measurements of an object to remove high-frequency noise, such as random variations and sensor noise. The filtered position measurements can then be used to compute the object's velocity and acceleration, which can provide useful information for predicting the object's future position and tracking its motion over time.

One common approach is to use a Kalman filter, which combines the Gaussian filter with a mathematical model of the object's motion to estimate its position and velocity. The Kalman filter uses the filtered position measurements to update its estimate of the object's state and predict its future position, based on the object's previous position and velocity.

Overall, Gaussian filter can be a powerful tool for motion tracking, as it can effectively remove high-frequency noise and improve the accuracy of position measurements, which is essential for reliable and robust tracking of moving objects.

[TODO: Put picture3]

**Kalman filter trajectory estimation**: The measurement - detection noise is set to a relatively high value, but the Kalman filter successfully predicts and corrects object trajectory. (Jurić, 2015)

# References

**Virtual Dance Mat Reference**

**Hand Jitter Reference**
