---
title: UI Design
layout: page
description: UI Design
---

## Sketches
  
After initial gathering of requirements, we drew some sketches.
  
![Sketches](../images/sketches.png)
  
As shown by the sketches, we planned to introduce a login system to the program where users can create accounts to save their personalised settings. They would be given the option to map the keys to their preferences and set the tremor sensitivity. We aimed to follow user requirements and human-computer interaction principles, thus making it simple, practical and obvious to use.
  
## Prototype
  
#### Initial prototype
  
We drew an initial prototype using figma. The pictures demonstrate how a user would set up the program and map keys.
  
![Ini](../images/initial_prototype.png)

#### Gaming Part
  
A visualization of how a user might play a game using their upper body or the virtual dance mat.
  
![Gaming](../images/proto_gaming.png)
  
#### Evaluation of prototype
  
We conducted a heuristic evaluation to find issues in our prototype.
  
![Heuristic](../images/heuristic.png)
  
Based on the evaluation, we altered the prototype to better fit requirements.
  
![Improv](../images/improv.png)
  
#### Final prototype
  
This was the final version of the prototype. The arrows colored in light blue are examples of directions from the navigation bar. The home button directs to the main menu, the question mark goes to the help video, and the logged-in profile image goes to settings. The gaming part remains the same.
  
![Final](../images/final_prototype.png)

  
## Implementation

During development and after learning newer requirements, we found several ways in which we needed to differ from the prototype.

![MainWindow](../images/ui_main_window.png)

In the main window, the users are able to choose from three modes. In the retro mode, the users can choose from a few controller templates that resemble the classic old-fashioned gamepads in real life, such as Nintendo NES and Sega Mega Drive. In the modern games mode, the users can create their own controller templates for the games they want to play. On the other hand, the mouse mode allows users to move the mouse cursor using the virtual dance mat and trigger mouse actions like left and right click, holding the left and right click, scrolling up and scrolling down using in-air action buttons. 

Moreover, the users have the option to turn on mouse tracking and choose to control mouse tracking using their left hands or right hands in the main window. At the same time, they can also choose the camera and to turn on or turn off FPS.

![ButtonsWindow](../images/ui_buttons_window.png)

When clicking on the In-Air Action Buttons button, the users will be led to the In-Air Action Buttons setting window. In this window, the users can choose to control the in-air action buttons using their left hands or right hands. Moreover, they can choose to select up to four in-air action buttons, the keys that the buttons trigger, whether to press the keys once or hold the keys, and the texts the buttons display. 

![DanceMatWindow](../images/ui_dance_mat_window.png)

When clicking on the Dance Mat Keys button, the Dance Mat Keys window will open. Similar to the In-Air Action Buttons window, the users can choose the keys the dance mat gestures trigger and whether to press the keys once or hold the keys.

When implementing the user interface, we made sure that the user interface was consistent and simplified. Therefore, the configuration wizard is straightforward and easy to use.
