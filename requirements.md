---
title: Requirements
layout: page
description: Requirements
---

# Team motivation

Computers have become an integral part of the gaming entertainment, providing gamers with an immersive and interactive experience, but there are many people who for a variety of physical health restraints which cannot interact with these devices in a traditional way. We recognized the opportunity of designing a software to be used in conjunction with MotionInput that would give them the ability to overcome these difficulties. By introducing flexible combinations of feet navigation and other gesture control. We will be giving our users a touchless gaming experience.

# Project Background

UCL MotionInput (MI) is a major software package launched globally for touchless computer interactions of nearly all ranges of human movement using just a webcam and PC. MI is a gesture and speech-based recognition layer for interacting with operating systems, applications, and games via just a webcam and PC. It is a pioneering touchless computing technology developed by UCL Computer Science students in collaboration with leading industry partners, Intel, Microsoft, IBM, Google, the NHS with Great Ormond Street Hospital for Children (GOSH DRIVE unit) and the UCLH Institute for Child Health.

Our team developed the first ever lower-body detection system upon the 3rd generation of UCL MotionInput.

# Client Introduction
Our primary stakeholders are **Prof. Dean Mohamedally** (UCL Computer Science Professor) and **Sheena Visram** (Great Ormond Street Hospital/UCL).

Additional stakeholders include:
* **Dr. Atia Rafiq** (NHS)
* **Prof. John McNamara** (IBM)
* **Prof. Joseph Connor** (NHS)
* **Costas Stylianou** (Intel)
* **Pippa Chick** (Intel)
* **Lee Stott** (Microsoft)
* **Cathy Cummings** (ALS/MND)

# Initial Project Objectives

1. Develop a dance-mat like interface for playing games with feet.
2. Implement a pose recognition algorithm to map gestures to keyboard or mouse events.
3. Create a mouse mode for the virtual dance mat that works with sitting and standing scenarios.
4. Integrate hand jitter correction technology to improve accuracy and user experience.
5. Provide a configuration wizard for customising features and setting jitter correction levels.

# Requirement gathering

After considering several methods of capturing requirements, we decided to conduct an online survey among our classmates and relatives, making sure of privacy protection for potential users. The survey **suggests respondents to put themselves in the perspective of care home residents** and imagine how would their experience be. We also conducted a semi-structured interview with NHS senior workers when they visited our lab session. Furthermore, we came to understand that the use case for this interactive system could be extended to all special needs groups, including special needs schools.

## Interview with NHS

**Q1**. Do you think there are adequate activity provided in the care home? Why do care home residents rarely use high-tech devices?  ​

**A1**. ​Most care homes provide a variety of activities, but residents do not have the same opportunities to participate due to various medical conditions. Providing sufficient and ongoing activity for everyone in care homes is still a challenge.​ There exists a gap of basic hardware supplies and professional accessibility software to choose from for care homes. Online games and smart devices offer colourful UI designs, nearly "too much" function, and user input, but the difficult user guide and a strong sense of unfamiliarity stop senior people from trying. ​

**Q2**. ​Do you think that technology can fulfil certain emotional needs that traditional care home activity is missing? ​​

**A2**. Yes, considering that Covid has made practically the entire society go towards a more virtual-friendly situation. At some point, the elderly has to use technology for communication and to interact with the outside world. In this case, software developers should put more effort into designing accessibility tools for special needs people.​

## Requirement Survey/Data collection​

The two images below show the responses to the two most important questions in the questionnaire. With real-time data and feedback, we can gauge the potential needs and expectations of the users and clarify the product features to focus on when designing the prototype.​

![](../images/survey1.png)
![](../images/survey2.png)

# Personas and Scenarios

After conducting user requirement research, we also talked to NHS senior workers and developed two personas for our target users in terms of different aspect: elderly and children; upper and lower body movement disorders. Our system provides gesture detection, jitter smoothing, speech recognition and leg detection.

![Persona1](../images/persona1.jpg)

## Scenario - Hank Dakmara (Elderly with Parkinson's)

​Hank likes chess but due to strong jitter, he had to stop playing it offline. Although he has little experience with online games, he decides to try online chess with the help of MI 3.2. He logged on to our system and followed a straightforward guide to how to use the gesture and speech recognition system. He can now decide where to place the move by **moving his hand in the air (in-range)**. His hand will still shake while moving, but with the help of our **strong jitter compensation algorithm**, counteracting the jitter and making the move smoother, he can concentrate on playing without worrying about making unintended moves. He can also use his voice. Our system will recognise if he speaks pre-defined keywords (e.g. pick and place) and apply them in the play. After a few rounds, he realises that our setting tutorial and control are easy and effective to use. According to the technology acceptance model by Davis[3]., we **maximised Hank’s perceived Usefulness and perceived Ease of Use**.​

![Persona2](../images/persona2.jpg)

## Scenario - ​Aoife Lous (Children with postural disorder)​

Aoife enjoys playing video games and is enthusiastic about IT and science. She has level II cerebral palsy, meaning she has impaired postural control, specifically on her lower body, she can't get her knees too high or her legs fully straight. She enjoys K-pop dancing and has tried out many of the dance machines in the game arcade. However, since the dance games like Dance Dance Revolution require intense physical movement, she could not even start to play the games. Therefore, she signed up for our system and had her first experience with the **virtual dance mat**. MI 3.2 uses the **coordinates** of her ankles and the **size of the pixels** they occupy to **determine the distance and depth** of her feet's movement. Her movements of ankle, feet and legs will be mapped to 9 buttons in the virtual dance mat so that she can trigger all buttons within a capable distance of her. With the help of our system, she can play dance games like others, and she has a very enjoyable playing experience.​

# Use cases

The functionality of FeetNav can be encapsulated in a concise set of use cases, which outline the actions a user might wish to perform. The accompanying diagram illustrates how these actions are subsequently transmitted as messages through the pipeline to the backend.

![UseCases](../images/use_case.png)

# Problems to solve and Solutions

| Problems | FeetNav Solutions |
| --- | --- |
| The gaming industry has limited accessibility for individuals with restricted upper-body movements. | A webcam-based **lower-body gestures recognition** system. |
| Using the MI gamepad mode for gameplay is not intuitive, as it requires the user to constantly switch their attention between the MI system windows and the game window. | A navigation system that used feet gesture to trigger the game hotkey, that uses a **dance-mat** based controller interface. User just need to move legs in forward, backwards, left, and right poses to trigger the game hotkey, and just focus on the game window. |
| While MI offers a broad range of gesture detection, users do not have the option to combine or use multiple navigation system simultaneously yet. | Introduced a configuration wizard program that will help users to add customed combinations of other body parts’ gesture control by simply clicking the ones they want to include. For example, hand hit-triggers. |
| Individuals with hand tremors are unable to use hand gestures detection system. | Introducing jitter correction algorithms for wrist tracking |

# MoSCoW requirement list

In order to ensure that our project meets the needs of our stakeholders, we conducted a thorough analysis of their requirements. Once we had a clear understanding of what was needed, we created a prioritised list of project objectives using the MoSCoW method. This helped us to focus on the most important goals first and enabled us to track our progress by regularly reviewing the list to see what had been accomplished. By using this approach, we were able to deliver a successful project that met the expectations of all stakeholders.

| ID| Requirements | Priority |
| --- | --- | --- |
| 1 | Dance-mat like interface that allows users to play games with their feets | Must |
| 2 | Mouse mode of the virtual dance mat | Must |
| 3 | Make the virtual dance mat compatible with both the standing and sitting scenario | Must |
| 4 | Pose recognition algorithm | Must |
| 5 | Map gestures to keyboard or mouse events | Must |
| 6 | Define the range of hand movements that need to be corrected, the speed and accuracy of correction | Must |
| 7 | Select the appropriate technology to achieve the required level of hand jitter correction. Prerequisite is the use of Mideapipe library | Must |
| 8 | Develop the hand jitter correction system, integrating the chosen technology into the mouse control layer of MotionInput 3.2 | Must |
| 9 | Best pose detection for the virtual dance mat | Should |
| 10 | Dance mat visualiser | Should |
| 11 | New display key for in-air action buttons | Should |
| 12 | Configuration wizard to allow users to customise FeetNav features | Should |
| 13 | Use design principles to optimise the configuration wizard | Should |
| 14 | Intuitive and aesthetically pleasing design | Should |
| 15 | Eliminate edge cases to optimise user experience | Should |
| 16 | Test the hand jitter correction to ensure that it meets the defined requirements. Evaluate the system's accuracy, speed, and user experience | Should |
| 17 | Refine the hand jitter correction system based on the testing results | Should |
| 18 | New display element for in-air action buttons | Could |
| 19 | Integrate the refined hand jitter correction system into every landmark of the hand module | Could |
| 20| User could set the level of jitter correction/ smoothing in the configuration wizard | Could |
