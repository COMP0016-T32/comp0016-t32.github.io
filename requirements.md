---
title: Requirements
layout: page
description: Requirements
---
  
## Project background and partner introduction
UCL MotionInput was conceptualized during COVID-19 and the first version was released in early 2021. It was a touchless computing platform designed to reduce phyiscal touch when interacting with computers to prevent the spreading of disease. Over the next 2 years its functionality and purposes have been expanded and added to by UCL Computer Science students, supported by the NHS and companies such as Microsoft, IBM and Intel.
This year, our group was tasked with contributing to version 3.2 of MotionInput, mainly towards facilitating elderly/disabled people in care homes with the ability to play different kinds of games using our gestures and accessiblity controls.
Our primary stakeholders are Prof. Dean Mohamedally (UCL Computer Science), John McNamara (IBM), Pippa Chick (Intel).

## Project Goals
- Expand MotionInput to the lower body, adding gestures and controls for ankles and feet and 
- a Virtual Dance Mat that can be tailored to user's needs and allows many games to be played
- Add jitter compensation algorithm to current hands module of MotionInput to allow people with Parkinson's/severe essential tremor to benefit

## Requirement gathering

### How did you collect the requirements?

After considering several methods of capturing requirements, we decided to conduct an online survey among our classmates and relatives, making sure of privacy protection for potential users. The survey suggest respondents to put themselves in the perspective of care home residents and imagine how would their experience be. We also conducted a semi-structured interview with NHS senior workers when they visited our lab session. Furthermore, we came to understand that the use case for this interactive system could be extended to all special needs groups, including special needs schools.​

### Did you design any survey? How did you analyse the survey data?

#### Interview with NHS staff
Q1. Do you think there are adequate activity provided in the care home? Why do care home residents rarely use high-tech devices?  ​

A1. ​Most care homes provide a variety of activities, but residents do not have the same opportunities to participate due to various medical conditions. Providing sufficient and ongoing activity for everyone in care homes is still a challenge.​ There exists a gap of basic hardware supplies and professional accessibility software to choose from for care homes. Online games and smart devices offer colourful UI designs, nearly "too much" function, and user input, but the difficult user guide and a strong sense of unfamiliarity stop senior people from trying. ​

Q2. ​Do you think that technology can fulfill certain emotional needs that traditional care home activity is missing? ​​

A2. Yes, considering that Covid has made practically the entire society go towards a more virtual-friendly situation. At some point, the elderly have to use technology for communication and to interact with the outside world. In this case, software developers should put more effort into designing accessibility tools for special needs people.​

#### Requirement Survey/Data collection​

The two images below show the responses to the two most important questions in the questionnaire. With real-time data and feedback, we can gauge the potential needs and expectations of the users and clarify the product features to focus on when designing the prototype.​

![Results](../images/results.png)

## Personas

![Persona1](../images/persona1.jpg)

### Scenario - Hank Dakmara (Elderly with Parkinson's)

​Hank likes chess but due to strong jitter, he had to stop playing it offline. Although he has little experience with online games, he decides to try online chess with the help of MI 3.2. He logged on to our system and followed a straightforward guide to how to use the gesture and speech recognition system. He can now decide where to place the move by moving his hand in the air (in-range). His hand will still shake while moving, but with the help of our strong jitter compensation algorithm, counteracting the jitter and making the move smoother, he can concentrate on playing without worrying about making unintended moves. He can also use his voice. Our system will recognise if he speaks pre-defined keywords (e.g. pick and place) and apply them in the play. After a few rounds, he realises that our setting tutorial and control are easy and effective to use. According to the technology acceptance model by Davis[3]., we maximised Hank’s perceived Usefulness and perceived Ease of Use.​

![Persona2](../images/persona2.jpg)

### Scenario - ​Aoife Lous (Children with postural disorder)​

Aoife enjoys playing video games and is enthusiastic about IT and science. She has level II cerebral palsy, meaning she has impaired postural control, specifically on her lower body, she can't get her knees too high or her legs fully straight. She enjoys K-pop dancing and has tried out many of the dance machines in the game arcade. However, since the dance games like Dance Dance Revolution require intense physical movement, she could not even start to play the games. Therefore, she signed up for our system and had her first experience with the virtual dance mat. MI 3.2 uses the coordinates of her ankles and the size of the pixels they occupy to determine the distance and depth of her feet's movement. Her movements of ankle, feet and legs will be mapped to 9 buttons in the virtual dance mat so that she can trigger all buttons within a capable distance of her. With the help of our system, she can play dance games like others, and she has a very enjoyable playing experience.​

## Use cases (if applicable)

### Use case diagram
### List of use cases

## MoSCoW requirement list

### Functional requirements:

| ID | Requirement                                     | Priority |
| -- | ----------------------------------------------- | -------- |
| 1  | Working virtual dance mat                       | Must     |
| 2  | Allow users to play retro games                 | Must     |
| 3  | Allow users to play fifa                        | Must     |
| 4  | Allow users to use speech commands and one hand | Must     |
| 5  | Algorithm for stabilizing hand jitter           | Must     |
| 6  | Gestures & controls for feet and ankles         | Must     |
| 7  | Kick height lines for fifa                      | Should   |

### Non-functional requirements: 

| ID | Requirement                                         | Priority |
| -- | --------------------------------------------------- | -------- |
| 8  | Compatible with MotionInput 3.2                     | Must     |
| 9  | Easy to use/fun for average user                    | Must     |
| 10 | Run on windows machines                             | Must     |
| 11 | Easy to extend for future developers                | Must     |
| 12 | Indicate virtual dance mat button presses on screen | Should   |
