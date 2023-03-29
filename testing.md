---
title: Testing
layout: page
description: Testing
---

# Testing strategy

Testing is very important to the development of a project as testing helps to identify defects and errors and ensures all the functionalities are working seamlessly. Throughout the development of our project, we have always applied user acceptance testing to ensure our product is functioning as intended. However, as our project is inherited from a large amount of legacy code, which is highly complicated with many interdependent components, we were unable to apply unit testing codes onto our project. Instead, we conducted something similar to unit tests and integration tests manually running program the program hundreds of times with different circumstances, for example, sitting, standing situations and different people, to make sure our implementation works correctly.

We also recognized the importance of hand jitter correction and collaborated with other teams who had similar needs, such as Team27 (bedside navigator) and Team38. Since our main focus is on lower body testing, our testing process for the system is primarily reflected in the lower body data, we acknowledged that testing hand data is more challenging for our team. Therefore, we collaborated with other groups who specialise in hand detection, and have more experience with hand position testing. This collaboration allowed us to improve the accuracy and effectiveness of our hand jitter correction techniques and ensure a more robust system overall.

# User Acceptance Testing

In the final stage of the development, user acceptance testing is applied to our project by extensively testing our product with a range of video games. These games fall into two big categories, which are retro games and modern games, and each of them differ slightly in terms of keyboard and mouse usage to ensure that we covered as many as edge cases as possible. Moreover, we also tested the Mouse Mode of our product with a web browser and Microsoft Paint.

![](../images/game_sheet.png)

As a result of the game tests, we concluded that our product is able to support all retro games that can be played with a gamepad with no more than four buttons. In other word, the FeetNav features are able to fully simulate the functionalities of two-button, three-button, and four-button gamepads, allowing users to enjoy gameplay using lower body movements and one hand. On the other hand, the support of the FeetNav features for modern games is limited to a small extent. While most casual modern games, such as Stardew Valley, are playable with the FeetNav features, the playability of the games that involve a lot of movements in a short period of time is limited as there is a processing time for MotionInput to recognise the gesture and trigger the corresponding gesture event, which in turn causes a delay in the movements of the game avatars. Moreover, the playability of such games also depends on the fitness level of the users as these games require a lot of physical movements from the users.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dexC76ql2b0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Hand Jitter Correction Testing

During the hand jitter correction testing phase, we collaborated closely with Team 27, the Beside navigator team, who also required the implementation of a hand jitter correction filter in their system. To ensure consistency and accuracy in their implementation, they adopted our approach and utilised the same algorithms for their testing. We found that the Laplacian smoothing and Gaussian filter techniques provided a much more stable hand tracking experience. The hand jitter detection capabilities of the filter were effective in accurately detecting and registering intentional button presses by the user, resulting in an overall improved user experience. The testing results for the Beside navigator team were positive, indicating the success of our joint efforts in developing and testing effective hand jitter correction techniques.
