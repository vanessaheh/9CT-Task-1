# 9CT Assessment task 1
### By Vanessa He

## Requirements Outline
 Write 2-3 sentences  explaining what your robot is designed to do in this challenge:

I need to design a program for the EV3 mindstorms robot where it navigates and picks up red and yellow blocks using the color sensor and bring them back to the starting zone while detecting and avoiding obstacles.

Identify key actions:
List at least 3-5 specific actions your robot needs to complete the task.

>1. pick up the red and yellow blocks
>2. if the obstacle detected is green or blue, it turns 90° degrees away and continues navigating
>3. navigate and bring the red and yellow blocks back to the starting zone
>4. shows that it has completed the task
### Functional Requirements
For each key action, write a functional requirement that clearly states what the robot must do. These should be written in a clear and concise manner.

- picking up the blocks: the robot must be able to spear and hook the red and yellow blocks onto itself

- obstacle avoidance: the robot must stop and turn 90°  when the ultrasonic sensor detects an object green or blue within 10 cm

- returning to the starting zone: the robot must be able to find and return back to the starting zone with the red and yellow blocks.

- finishing: the robot must be able to show that it has completed the task

## Non-functional requirements
These are requirements that focus on how well the robot will perform in completing the task, rather than the completing of the task itself.

Efficiency:
The robot must be able to complete the task in under five minutes

Response time:
The robot must respond and perfrom the next set of actions within 1 second 

Accuracy:
The robot must be able to accurately identify the colour and retrieve the blocks into the starting zone without going outside of the mat

## Use Cases
1. **Picking up the red and yellow blocks**

Scenario: The robot comes in contact with the red or yellow blocks.

Input: the robot uses the colour sensor to make sure it is red or yellow

Action: after confirming, the robot moves forward and spears hollow centre of the block to hook onto itself

Expected outcome: The block has been speared and the robot is able to move with the block connected

2. **Obstacle avoidance:**

Scenario: The robot comes into contact with an obstacle

Input: The ultrasonic sensor detects an object within 10 cm

Input: The colour sensor identifies the colour of the obstacle

Action: If the object is green or blue, the robot turns 90° to avoid the obstacle

Expected outcome: The robot avoids the obstacle and continues its path

3. **Navigation and retrieving the red and yellow blocks**

Scenario: The robot has speared the yellow/ red block and must navigate the starting zone

Input: The robot identifies which block has been picked up using the colour sensor

Action: The robot runs the specific route for the coloured block to get back to the starting zone

Expected outcome:
The robot is able to find and go back to the starting zone with the block

4. **Finishing:**

Scenario: The robot finishes with the blocks in the finish line

Input: The robot checks if it has done two runs to the finish line

Action: Using the display function, the screen says "Finished!" when the task is completed screen says 

Expected outcome: It is able to display "Finished" to show it has completed the task

## Test Cases

| Test Case | Input     | Expected Output   |
|---------- |---------- |----------------   |
| Picking up blocks| the robot identifies the block colour| Moves forward and spears the red and yellow block
| Retrieving the red and yellow blocks| runs a different code for each block to navigate the starting zone| robot is able to find and deliver the block to the starting zone
Avoids obstacle| ultrasonic sensor detects <10 cm| robot stops and turns 90° | 
| Finishing | the robot checks if it has done two runs to the starting zone with the blocks | if true, the robot displays "finished"               |

## Pseudocode development


### Flowcharts


## Development and Integration

```Python
#BEGIN
print("Hello World!")
```