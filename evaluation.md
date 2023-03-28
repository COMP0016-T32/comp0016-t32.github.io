---
title: Evaluation
layout: page
description: Evaluation
---

# Summary of Achievements

## Final MoSCoW Requirements Review

| ID | Requirement | Priority | State | Contributors |
| --- | --- | --- | --- | --- |
|1|Dance-mat like interface that allows users to play games with their feets|Must|✓|Dongyeon, Minghui, Tina, Team 26|
|2|Mouse mode of the virtual dance mat|Must|✓|Minghui|
|3|Make the virtual dance mat compatible with both the standing and sitting scenario|Must|✓|Dongyeon|
|4|Pose recognition algorithm|Must|✓|Dongyeon, Minghui|
|5|Map gestures to keyboard or mouse events|Must|✓|Dongyeon, Minghui|
|6|Define the range of hand movements that need to be corrected, the speed and accuracy of correction|Must|✓|Tina|
|7|Select the appropriate technology to achieve the required level of hand jitter correction. Prerequisite is the use of Mideapipe library|Must|✓|Tina|
|8|Develop the hand jitter correction system, integrating the chosen technology into the mouse control layer of MotionInput 3.2|Must|✓|Tina|
|9|Best pose detection for the virtual dance mat|Should|✓|Dongyeon, Minghui|
|10|Dance mat visualiser|Should|✓|Dongyeon, Minghui|
|11|New display key for in-air action buttons|Should|✓|Dongyeon, Minghui|
|12|Configuration wizard to allow users to customise FeetNav features|Should|✓|Dongyeon, Minghui|
|13|Use design principles to optimise the configuration wizard|Should|✓|Dongyeon|
|14|Intuitive and aesthetically pleasing design|Should|✓|Dongyeon, Minghui|
|15|Eliminate edge cases to optimise user experience|Should|✓|Dongyeon, Minghui|
|16|Test the hand jitter correction to ensure that it meets the defined requirements. Evaluate the system's accuracy, speed, and user experience|Should|✓|Tina|
|17|Refine the hand jitter correction system based on the testing results|Should|✓|Tina|
|18|New display element for in-air action buttons|Could|✓|Dongyeon|
|19|Integrate the refined hand jitter correction system into every landmark of the hand module|Could|✓|Tina|
|20|User could set the level of jitter correction/smoothing in the configuration wizard|Could|✗||

## A list of known bugs

| ID | Bug Description | Priority |
| --- | --- | --- |
|1| | |

## Individual contribution distribution table

| Work packages | Dongyeon | Minghui | Tina | Ali |
| --- | --- | --- | --- | --- |
| Project partner liasion | | | | |
| Requirement analysis | | | | |
| Research and Experiments | | | | |
| UI Design | | | | |
| Coding | | | | |
| Testing | | | | |
| Report Website | | | | |
| Video Editing | | | | |
| Overall contribution | | | | |
| Main roles | | | | |

# Critical evaluation of the project

## User experience

Overall, our product is easy to learn and intuitive to use. The configuration wizard also allows users to customise our product to apply it over a large range of activities, such as gaming, web browsing, and drawing. 

## Functionality 

We have fulfilled all the key requirements and tried our best to come up with as many optional requirements as possible to optimise user experience. In the end, every component of our product is fully functional and can be effectively integrated with one another.

## Stability

The virtual dance mat is 95% stable. The leftward and rightward leg movements are always stable and are rarely triggered by mistake. However, as the depth of the landmarks from the camera is an estimation by MediaPipe, the forward and backward leg movements are less stable as the distance between the two feet is sometimes miscalculated.

## Efficiency

Throughout the development of the project, we have applied various design principles to ensure the efficiency of the codes. As a result, our final product can almost synchronise users’ movements and the corresponding keyboard and mouse events. There is only a slight delay as there are many layers in the MotionInput legacy codes to process the raw image.

## Compatibility

As all the FeetNav features can be used without the Internet and the configuration wizard is developed using MFC, which is commonly used for developing desktop applications for Windows, all the FeetNav features are able to work across all Windows devices. 

## Maintainability 

As all of our work was shared across the group, every member tried to make additions that were organised and well-documented. Moreover, our codes were constantly refined so that they were efficient and concise. 

## Project Management

With the help of various planning tool, we managed our time well and were able to deliver all products by time. Moreover, we often met up to discuss our progress to make sure that everyone was up to date with the latest information. Peer programming was often used in our group to generate codes of high quality.

# Future work

## 1. Add gestures in the four diagonal directions

Nowadays, a lot of dance mats in the market are a 3x3 grid and support eight buttons. Therefore, pose detection algorithms for leg movements in the four diagonal directions can be added so that our product can simulate the full functionalities of a modern dance mat.

## 2. Gesture recorder for lower body movements

For the moment, the virtual dance mat only supports four keyboard or mouse events. Therefore, it is impossible to play a lot of games with only lower body movements. If a gesture recorder were added to allow users to map more gestures, such as a kicking gesture, to more keyboard events or mouse events, it is possible to slowly remove the in-air action buttons so that our product can be used by a wider range of users. For example, this will allow users with no arms to play games with our product.
