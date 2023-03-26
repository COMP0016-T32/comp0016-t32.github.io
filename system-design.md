---
title: System Design
layout: page
description: System Design
---

![](../images/system_design1.png)

The diagram above shows the basic components of the system and the flow of interaction/data between them.

The system can be divided into 5 main categories:
* **User**: The user is the person who is using the system. The user can use MotionInput by moving their body.
* **MotionInput Front-End**: Front-end side is where users can actually see and interact with MotionInput. Users can see the buttons and other visuals on the screen and interact with them by moving their body.
* **MotionInput Back-End**: Back-end side controls the judgement of the user's motion with MediaPipe's Pose solution and Virtual Dance Mat, and sends the result to either the gameplay layer or mouse control layer depending on the user's setting. The layers press the key input and also trigger the dance mat visualiser which controls the front-end side.
* **Configuration Wizard**: Using the separate program written in MFC, the user can change the mode for different games because different games require different settings. Some games might require the mouse tracking feature or another game might require 4 in-air action keys. Users can change the setting easily by clicking several times and save, load, or delete the settings.
* **Data Store**: Storing the data plays an important role since every setting of users and other system data needed to run MotionInput seamlessly are stored in files. `config.json` file stores the general system data for MotionInput such as whether showing FPS and which camera to use in MotionInput.

![](../images/system_design2.png)

The diagram above is another way to show our system design. Additional component shown here is Hand Jitter Stabilisation which deals with severe hand jittering to increase the accuracy of the system.