# 9CT Assessment task 1
### By Vanessa He

## Requirements Outline
 Write 2-3 sentences  explaining what your robot is designed to do in this challenge:

I need to design a program for the EV3 mindstorms robot where it navigates and picks up red and yellow blocks using the color sensor and bring them back to the starting zone while detecting and avoiding obstacles.

Identify key actions:
List at least 3-5 specific actions your robot needs to complete the task.

1. pick up the red and yellow blocks
2. detect the colours of the blocks and obstacles
3. if the obstacle detected is green or blue, it turns 90° degrees away and continues navigating
4. navigate and bring the red and yellow blocks back to the starting zone

### Functional Requirements
For each key action, write a functional requirement that clearly states what the robot must do. These should be written in a clear and concise manner.

- picking up the blocks: the robot must be able to spear and hook the red and yellow blocks onto itself

- colour detection: the robot must be able to detect the colour of the blocks and obstacles using the colour sensor

-  obstacle avoidance: the robot must stop and turn 90°  when the ultrasonic sensor detects an object green or blue within 10 cm

- returning to the starting zone: the robot must be able to find and return back to the starting zone with the red and yellow blocks.

## Non-functional requirements
These are requirements that focus on how well the robot will perform in completing the task, rather than the completing of the task itself.

Efficiency:
The robot must be able to complete the task in under five minutes

Response time:

Accuracy:

## Use Cases
1. Picking up the red and yellow blocks

Scenario: The robot comes in contact with the red or yellow blocks.

Inputs:

Actions: The robot moves forward and captures the block by spearing the hollow middle.

2. detecting the colour of the blocks and obstacles

Scenario: The robot comes in contact with a block or an obstacle

Input: The colour sensor identifies the colour of the obstacle 

Action: 

3. Obstacle avoidance:

Scenario: The robot comes into contact with an obstacle

Input: The ultrasonic sensor detects an object within 10 cm

Input: THe colour sensor identifies the colour of the obstacle

Action: If the object is green or blue, the robot turns 90° to avoid the obstacle

Expected outcome: The robot avoids the obstacle and continues its path


Inputs: The u

## Test Cases

| Test Case | Input     | Expected Output   |
|---------- |---------- |----------------   |
| Avoids obstacle          |           |                   |
|   R        |           |                   |
|           |           |                   |




```Python
#BEGIN
print("Hello World!")
```
### Flowcharts


## Development and Integration
