---
title: Research
layout: page
description: Research
---
  
## Related projects
  During our research, we didn't find any project doing our aim which is using a webcam to emulate a dance mat. However we found a slightly related project that uses vive trackers to make a virtual dance pad.

## Literature review
  Biological review on conditions that may affect people which would incentivize them to use our software. We conducted an interview with NHS staff and looked into causes of hand tremor e.g. parkinsons/essential tremor and the different severity and frequencies, and into paralysis/movement disorders such as ALS/MND, cerebral palsy. 
  
  Free/open source libraries.
  The best option we found was MediaPipe, which was already used in MotionInput. It fits the requirements, could be trained and is fast/reliable. However, the
  MediaPipe limitation is that it requires the face to be in camera. Therefore the whole body has to be visible and have to go far back, and multiple people can't be in camera.

  (literature review video)

## Technical decisions
  
MediaPipe & OpenCV. Pose module for pose estimation for virtual dance mat. Hands module & median-based filtering for hand jitter compensation.

## References
  
https://github.com/Reimajo/StepmaniaVR  
https://google.github.io/mediapipe/solutions/pose.html  
https://opencv.org/  
https://www.youtube.com/watch?v=06TE_U21FK4  
https://www.aafp.org/pubs/afp/issues/1999/0315/p1565.html  
https://www.aafp.org/pubs/afp/issues/2018/0201/p180.html  
https://academic.oup.com/ageing/article/51/7/afac135/6625704  
https://google.github.io/mediapipe/solutions/hands.html  
