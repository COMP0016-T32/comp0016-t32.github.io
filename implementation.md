---
title: Implementation
layout: page
description: Implementation
---

## 1.1 Pose Recognition Algorithm

The most important component of the virtual dance mat is to recognise the four 
gestures, which, namely, are the forward, backward, leftward, and rightward 
movements of users’ legs. To achieve this, we used the landmarks returned by 
MediaPipe Pose Solution to calculate the distance between the two legs and the 
distance between the hip and a leg. We found the best landmarks to track and the
 threshold for the gestures to become active through trial and error.

![Pose Recognition Algorithm](../images/body_landmarks.png)

When the users perform the gestures, the coordinates of their landmarks will 
always differ slightly. Hence, to find the best landmarks to calculate the 
distance, we tried a number of combinations and calculated the distance between 
them. For every combination, we asked five different testees to perform the 
gestures 20 times and calculated the average.

***Test result of forward and backward leg movements***

| Combination | Fluctuation |
|-------------|-------------|
|Left hip and right foot index | 0.005 |
|Left ankle and right foot index | 0.004 |
|Left foot index and right foot index |	0.001 |

***Test result of leftward leg movement***

| Combination | Fluctuation |
|-------------|-------------|
|Left hip and left foot index | 0.003 |
|Left hip and left ankle| 0.001 |

***Test result of rightward leg movement***

| Combination | Fluctuation |
|-------------|-------------|
|Right hip and right foot index | 0.004 |
|Right hip and right ankle| 0.0015 |

As a result of the tests, we decided to use the distance between the left foot 
index and the right foot index to determine if the forward and backward leg 
movements are activated, the left hip and left ankle for leftward leg movement, 
and the right hip and the right ankle for rightward leg movement.

After confirming the landmarks to use, our second task was to find a threshold 
for every gesture so that whenever the distance between the respective landmarks
 of the gesture becomes larger than the threshold, the gesture will be 
 considered active. Again, we tested a range of thresholds with five different 
 testees performing the gestures 20 times and took the average.

***Test result of forward leg movement***

| Threshold | Accuracy |
|-------------|-------------|
|0.15 | 80% |
|0.13| 95% |
|0.11| 90% |
|0.09| 85% |
|0.07| 75% |

***Test result of backward leg movement***

| Threshold | Accuracy |
|-------------|-------------|
|0.13 | 95% |
|0.10| 90% |
|0.07| 85% |
|0.06| 85% |
|0.03| 75% |

***Test result of leftward leg movement***

| Threshold | Accuracy |
|-------------|-------------|
|50 | 80% |
|40| 80% |
|30| 90% |
|25| 95% |
|20| 90% |

***Test result of rightward leg movement***

| Threshold | Accuracy |
|-------------|-------------|
|50 | 95% |
|40| 90% |
|30| 90% |
|25| 85% |
|20| 85% |

In these tests, we define accuracy as the user’s action will be recognised as the correct gesture. For example, when the user moves his right leg forward, the gesture will be recognised as forward gesture activated instead of forward gesture not activated or rightward gesture activated. As a result of the tests, we concluded that 0.13 is the best threshold for the forward and backward leg movement, 25 for the leftward leg movement, and 50 for the rightward leg movement.

Combining the results of the two tests, we developed the following algorithms for the four gestures.

```python
class BackFootPose(BodyPose):
    def check(self, landmarks: dict) -> bool:
        try:
            legs_depth_diff = landmarks["right_foot_index"][2] - landmarks["left_foot_index"][2]
            self.score = int(legs_depth_diff < -0.15)
        except KeyError:
            self.score = 0

        return self.score == 1
```

```python
class FrontFootPose(BodyPose):
    def check(self, landmarks: dict) -> bool:
        try:
            legs_depth_diff = landmarks["right_foot_index"][2] - landmarks["left_foot_index"][2]
            self.score = int(legs_depth_diff > 0.15) 
        except KeyError:
            self.score = 0

        return self.score == 1
```

```python
class RightFootPose(BodyPose):
    def check(self, landmarks: dict) -> bool:
        try:
            right_leg_movement = landmarks["right_hip"][0] - landmarks["right_ankle"][0]
            self.score = int(right_leg_movement > 25)
        except KeyError:
            self.score = 0

        return self.score == 1
```

```python
class LeftFootPose(BodyPose):
    def check(self, landmarks: dict) -> bool:
        try:
            left_leg_movement = landmarks["left_ankle"][0] - landmarks["left_hip"][0]
            self.score = int(left_leg_movement > 50)
        except KeyError:
            self.score = 0

        return self.score == 1
```

<!-- ![](../images/foot_back_before.png)
![](../images/foot_front_before.png)
![](../images/foot_right.png)
![](../images/foot_left.png) -->

## 1.2 Best Pose Detection

After defining the criteria to determine if the gestures are active, we encountered another problem, which was the incorrect gesture would be triggered sometimes. For example, when the users move their leg forward, the leftward leg movement will be triggered instead. To solve the problem, we decided to add more conditions when determining the score for the gestures. In the end, we changed the algorithms so that the forward and backward leg movements will only be determined as active if they fulfil the criteria of the forward and backward leg movements and do not fulfil the criteria of the leftward and rightward leg movements. This improved the accuracy of our pose detection.

![](../images/foot_back.png)
![](../images/foot_front.png)

## 1.3 Key Mapping and Dance Mat Visualiser

In the superclass of the four gesture classes, Pose, we defined the logic of key mapping and dance mat visualiser. To make sure the action types “key_down” (hold the key) and “key_press” (press the key once) are triggered correctly, we used two boolean variables to track the status of the gestures. The variable “state” turns true when the gesture becomes active and trigger the “key_down” event. As the gesture continues to be active, the variable “activated” will be checked every frame. “activated” will be turned true when “key_pressing” event happens and will remain true throughout the period where the gesture is active so that the “key_pressing” event will only happen once in this period. In the deactivating stage, both variables will be turned false.

![](../images/abstract_pose.png)

The DanceMatVisualiser class we created is a singleton class which defines the logic to draw the dance mat display elements on the upper left corner of the MI window and change the colour of the display elements when the gestures become active. The instance of DanceMatVIsualiser is created in Pose to update the display elements when the status of the gestures changes.

![](../images/dance_mat_visualiser.png)

# 2. In-Air Action Buttons

## 2.1 New Display Element
Initially, the colour of the buttons is red when not activated and green when activated, which is not aesthetically pleasing and intuitive. Therefore, we designed a new appearance of the buttons using Vectornator. The new display of the buttons features 3D light blue buttons when they are not pressed, and they will turn light yellow when activated. The new buttons resemble the buttons on gamepads and are much more visually appealing.

When we first replaced the original buttons with the images we designed, we found that the activation area of the buttons was much larger than the buttons themselves, which means the users can activate the buttons by moving their wrists close to the buttons instead of overlapping their wrists with the buttons. To correct the situation, we decreased the radius parameter in config.json so that the activation area is the same size as the images of the buttons.

![](../images/original_inair_buttons.png)
***Original version of the in-air action buttons***
 
![](../images/improved_inair_buttons.png)
***Improved version of the in-air action buttons***

## 2.2 New Display Key

Originally, the texts in the buttons were integers that record the number of the times that the buttons are pressed. This was very hard for the users to understand and did not convey any information of which keys the buttons were mapped to. Hence, we decided to add a new display key to the buttons so that they display the key that they are mapped to. A new displaykey parameter in the json files that record the parameters of the buttons, and the displaykey parameter is loaded from the json files and provided as input to the display element function of the in-air action buttons. 

[TODO: (original buttons with counters)]

# 3. Mouse Tracking

In mode_controller.json, we defined two new modes, the left mode and the right mode, which contain our combination of mouse tracking events. The left mode allows users to control the mouse using their left hand while the right mode allows users to control the mouse using their right hand. To trigger a left click, the users need to make a gun shape with their hands, which is to stretch out their thumbs and index fingers and curl the rest of the fingers towards their palms. On the other hand, to trigger a right click, the users need to pitch their middle fingers, which is to put their middle fingers and their thumbs together. The addition of these two modes made the configuration of the virtual dance mat easy.

![](../images/mode_controller.png)

# 4. Configuration Wizard

## 4.1 GlobalStatus

To pass the values of variables, such as the key mapping and key action of the in-air action buttons and dance mat keys, between different dialog windows, a singleton class GlobalStatus was used. An instance of the GlobalStatus class was created and passed into the C++ files of the dialog windows, and thus the in-air action buttons dialog window and the dance mat keys dialog window will be able to store the values of variables set by the users and the main setting dialog window will be able to access these values and save them to the mode json file and the config json file.

## 4.2 Error Handling

To maximise user experience, we put in effort to eliminate edge cases. We have covered the following edge cases:

For convenience, the current mode selected in MotionInput is shown when the users open the configuration wizard.

When no controller template is selected from the drop down list and the users click the Launch button, an alert message will be shown to prompt the users to choose a controller template. 

When the users are not in the edit mode, the Apply button, which is used to save changes, is disabled. Moreover, every button in the Mouse Tracking section, the In-Air Action Button dialog window and the Dance Mat Keys dialog window is disabled to prevent the users from accidentally changing the settings.

When in the edit mode, the users will only be able to change the key mapping, key action and display of the buttons if the button is selected. Otherwise, those drop down lists and input fields will be disabled. This is to reduce confusion so that the users will not set any buttons that they have not selected.

In adding a new mode window, after the users enter the name for the new controller template, the program checks if the name contains any special characters or if the controller template already exists. This is to prevent errors when creating the json file for the new controller template.


# 5. Hand jitter Correction

## 5.1 Smoother Class in Mouse Event Handler

In MotionInput 3.2, the gesture_event_handlers folder already includes desktop_mouse.py for handling cursor movement events. The implementation logic for triggering specific actions based on these events is entirely defined by the update function within the event class. For instance, if the user has just activated the mouse control gesture in the current frame and it was not previously held, the logic of the update function will set it to the "activated" state and execute the corresponding function mapped to the cursor movement event handler. This approach enables us to map user actions to device actions.

The event class "BaseMouse" serves as a generic class for handling cursor movement events. Although the original intention of MI 3.2 codebase was to smooth out the coordinates of the mouse movement, the current implementation only uses the average coordinates of the last few frames. However, there could be alternative and more efficient approaches to achieve this smoothing effect.

## 5.2 Capturing the coordinates from past frames

To implement any smoothing algorithm, we must first obtain the past data of the user's hand position coordinates and feed it into the smoothing function to calculate the averaged value. The primary goal is to create an extra layer of filtering between the RAW mouse coordinates (mapped based on the hand landmarks on the screen) and the output x and y coordinates to effectively move the cursor on the user's device. This additional layer of filtering ensures that the cursor movements are smooth and accurate, providing a better user experience.

To do that, we created a smoothing buffer to store the RAW DATA from past frames, and store it as a NumPy array namely “tracking_points”. Once we have more than three frames’ coordinates we apply the smoothing algorithms – Laplacian smoothing and Gaussian filter.

![](../images/smoother_class.png)

Three coordinates from the past frame can be sufficient for smoothing calculation because they provide enough information to calculate a smoothed position. Averaging out the previous three coordinates can help to eliminate any sudden or jittery movements caused by hand tremors or other factors. Using more coordinates from the past frames could lead to increased processing time and potential lag, without significantly improving the smoothing effect. Additionally, using too many past coordinates may also result in a delayed response to user movements, which could negatively impact the user experience. Therefore, using a small number of coordinates from the past frames can strike a balance between reducing jitter and maintaining responsiveness.

## 5.3 Laplacian smoothing and Gaussian filter

![](../images/smoothing_algorithms.png)

The Python code above implements two different techniques for smoothing tracking points in desktop_mouse.py.
The first technique is called Laplacian smoothing, and it involves calculating the mean of each tracking point and its neighbours. The implementation works as follows:
- The tracking points are converted to a NumPy array and stored in the tracking_points variable.
- A zero-filled NumPy array of the same size as tracking_points is created and stored in smoothed_points.
- The mean of each point and its neighbors is then computed using the formula (tracking_points[:-2] + tracking_points[1:-1] + tracking_points[2:]) / 3.
- The computed mean is stored in the corresponding position in the smoothed_points array, except for the first and last points.
- The first point is smoothed by taking the average of the first two points, and the last point is smoothed by taking the average of the last two points.
- The function then returns the smoothed_points array.

The second technique is called Gaussian smoothing, and it involves applying a Gaussian filter to the tracking points. The implementation works as follows:
- The tracking points are converted to a NumPy array and stored in the tracking_points variable.
- The gaussian_filter function from the SciPy library is applied to the tracking_points array with a sigma value of 1, which determines the width of the Gaussian filter.
- The smoothed array is then returned by the function.
Both of these smoothing techniques can be effective for reducing noise and jitter in hand position tracking data, and can improve the overall user experience in MotionInput.
