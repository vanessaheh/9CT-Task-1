# 9CT Assessment task 1

### By Vanessa He

## Requirements Outline
 Write 2-3 sentences  explaining what your robot is designed to do in this challenge:
### Defining the purpose
I need to design a program for the EV3 mindstorms robot where it navigates and picks up red and yellow blocks using the color and ultrasonic sensor and bring them back to the starting zone while detecting and avoiding obstacles.

### Identify key actions:
List at least 3-5 specific actions your robot needs to complete the task.

>1. pick up the red and yellow blocks.
>2. if the obstacle detected is green or blue, it turns 90° degrees away and continues navigating.
>3. navigate and bring the red and yellow blocks back to the starting zone.
>4. shows that it has completed the task.

### Functional Requirements
For each key action, write a functional requirement that clearly states what the robot must do. These should be written in a clear and concise manner.

- picking up the blocks: the robot must be able to spear and hook the red and yellow blocks onto itself.

- obstacle avoidance: the robot must stop and turn 90°  when the ultrasonic sensor detects an object green or blue within 10 cm

- returning to the starting zone: the robot must be able to find and return back to the starting zone with the red and yellow blocks.

- finishing: the robot must be able to show that it has completed the task.

### Non-functional requirements
These are requirements that focus on how well the robot will perform in completing the task, rather than the completing of the task itself.

Efficiency:
The robot must be able to complete the task in under five minutes.

Response time:
The robot must respond and perfrom the next set of actions within 1 second.

Accuracy:
The robot must be able to accurately identify the colour and retrieve the blocks into the starting zone without going outside of the mat.

### Use Cases
1. **Picking up the red and yellow blocks**

Scenario: The robot comes in contact with the red or yellow blocks.

Input: the robot uses the colour sensor to make sure it is red or yellow.

Action: after confirming, the robot moves forward and spears hollow centre of the block to hook onto itself.

Expected outcome: The block has been speared and the robot is able to move with the block connected.

2. **Obstacle avoidance:**

Scenario: The robot comes into contact with an obstacle.

Input: The ultrasonic sensor detects an object within 10 cm.

Input: The colour sensor identifies the colour of the obstacle.

Action: If the object is green or blue, the robot turns 90° to avoid the obstacle.

Expected outcome: The robot avoids the obstacle and continues its path.

3. **Navigation and retrieving the red and yellow blocks**

Scenario: The robot has speared the yellow and red blocks and must navigate the starting zone.

Input: The robot identifies which block has been picked up using the colour sensor.

Action: The robot runs the specific route for the coloured block to get back to the starting zone.

Expected outcome:
The robot is able to find and go back to the starting zone with the block.

4. **Finishing:**

Scenario: The robot finishes with the blocks in the finish line.

Input: The robot checks if it has done two runs to the finish line.

Action: Using the display function, the screen says "Finished!" when the task is completed.

Expected outcome: It is able to display "Finished" to show it has completed the task.

### Test Cases

| Test Case | Input     | Expected Output   |
|---------- |---------- |----------------   |
| Picking up blocks| the robot identifies the block colour| Moves forward and spears the red and yellow block
| Retrieving the red and yellow blocks| runs a different code for each block to navigate the starting zone| robot is able to find and deliver the block to the starting zone
Avoids obstacle| ultrasonic sensor detects <10 cm| robot stops and turns 90° | 
| Finishing | the robot checks if it has done two runs to the starting zone with the blocks | if true, the robot displays "finished"               |


### Flowcharts + Psudocode development
![alt text](<Screenshot 0007-05-18 at 11.44.15 pm.png>)

```
BEGIN
    detect_object
    colourcollect_yellow
    colourcollect_red
    drive_home
    display_finished
END
``` 
![alt text](<Screenshot 0007-05-18 at 11.45.25 pm.png>)
```
BEGIN detect_object
    WHILE distance > 100mm
        READ distance
        Drive Forwards
    ENDWHILE
    Turn right 90 degrees
END detect_object
```
![alt text](<Screenshot 0007-05-19 at 12.20.27 am.png>)
```
BEGIN colourcollect_yellow
    WHILE colour != yellow
        Drive Forwards
        READ colour
    ENDWHILE
    Drive forwards
END colourcollect_yellow
```
![alt text](<Screenshot 0007-05-19 at 12.21.40 am.png>)
```
BEGIN colourcollect_red
    WHILE colour != red
        Drive Forwards
        READ colour
    ENDWHILE
    Drive forwards
END colourcollect_red
```
![alt text](<Screenshot 0007-05-19 at 12.11.34 am.png>)
```
BEGIN display_finished
    WHILE NOT returned_with_both_red_and_yellow
        Check again
    
    ENDWHILE
    print "finished"
END display_finished
```
### Test Cases

```
# TEST 1
# Play a beep sound to signal the program has started
ev3.speaker.beep()

# The robot drives continuously unless an obstacle is detected to be within 15 cm
while True:
    robot.drive(200, 0)
   
# If an obstacle is detected within 15 cm, the robot waits 3 seconds, goes back 10 cm, turns to the right, drives 25 cm then turns back to the left to begin driving continuously again.
    if obstacle_sensor.distance() < 150:
        wait(3)
        robot.straight(-100)
        robot.turn(90)
        robot.straight(250)
        robot.turn(-90)

```
The robot didn't detect the wall fast enough and started rotating and moving on the wall. To solve this issue, we will need to make the "obstacle_sensor.distance()" larger so that the robot can detect obstacles from a distance and avoid bumping into them.

**Working Towards:**
- Making the "obstacle_sensor.distance()" larger
- Changing the "while True" to "while collected_obstacles < 2" when we start combining all the test cases.
---
```
# TEST 2
# Play a beep sound to indicate the program has started
ev3.speaker.beep()


# The robot drives continuously unless there's a break in the loop
while True:
    robot.drive(200, 0)


# If an obstacle is detected within 30 cm, the robot waits 3 seconds, goes back 10 cm, turns to the right, drives 15 cm then turns back to the left to begin driving continuously again.
    if obstacle_sensor.distance() > 300:
        wait(3)
        robot.straight(-100)
        robot.turn(90)
        robot.straight(150)
        robot.turn(-90)
```
**LATER NOTE:**
 This test case was intially going to be combined with the green/blue obstacle evasion in the end but we have decided to go with a different approach so we will only be needing the first half of this code with the robot driving, detecting the obstacle and pausing.

 > #### Evaluate your process in solving this test case.
 > This test case was the most successful, probably because it was the simplest. Most of this test case, including the obstacle being detected and avoiding it, went according to plan and we only had to a bit of measurement tweaking for it to work well. However, this was not used in our final program, as we identified later on that it would be easier to code the robot to go directly up to the red/yellow blocks and detect it there instead, as the robot could run off the map after its avoided all obstacles. We could have improved this test case by programming it to avoid obstacles while also checking that it remains in the map, but we didn't have enough time.


###  2. Green/Blue Obstacle Evasion (unused in final code)
| Input | Process | Output|
|---------- |---------- |----------------   |
| Ultrasonic sensor detects obstacle within 15 cm distance while the colour sensor detects the obstacle is green or blue | Robot reverses, moves sideways, then returns to original path | Robot evades green and blue obstacles
```
# TEST 1
# Play a beep sound to signal the program has started
ev3.speaker.beep()


# The robot drives continuously unless there's a break in the loop
while True:
    robot.drive(200, 0)


    # If an obstacle is detected within 30 cm, wait 3 seconds
    if obstacle_sensor.distance() < 300:
        wait(3)
        # If the colour sensor detects blue, beep twice then break the while loop
        if colour_sensor.color() == Color.BLUE:
           ev3.speaker.beep()
           ev3.speaker.beep()
           break
        # If the colour sensor detects green, beep twice then break the while loop
        elif colour_sensor.color() == Color.GREEN:
           ev3.speaker.beep()
           ev3.speaker.beep()
           ev3.speaker.beep()
           break
        else:
           ev3.speaker.beep()
           break
```
We must begin this test case by figuring out how to use the colour sensor so that it detects green and blue obstacles. We tested the code but it goes straight to the else statement, so the issue is probably in how we wrote "colour_sensor.color() == Color.X".


We did some research and found that the distance and sensor should around 3cm close for accurate colour detection so we'll decrease the "obstacle_sensor.distance" as well.


**Working Towards:**
- Figuring out how to make the colour sensor detect green and blue
- Changing the code to fit the original program plan once we identify and fix the issue with the colour sensor.
---
```
# TEST 2
# Play a beep sound to signal the program has started
ev3.speaker.beep()


# The robot drives continuously unless there's a break in the loop
while True:
    robot.drive(200, 0)


    # If an obstacle is detected within 15 cm, wait 3 seconds
    if obstacle_sensor.distance() < 150:
        wait(3)
        # If the colour sensor detects blue, beep twice then break the while loop
        if colour_sensor.color() == Color.BLUE:
           ev3.speaker.beep()
           ev3.speaker.beep()
           break
        # If the colour sensor detects green, beep three times then break the while loop
        elif colour_sensor.color() == Color.GREEN:
           ev3.speaker.beep()
           ev3.speaker.beep()
           ev3.speaker.beep()
           break
        else:
           ev3.speaker.beep()
           break
```
We changed the distance to 15 cm, but it still goes to the else statement when we have a green or blue obstacle, so its most likely a problem with how the if and elif statements are written. To solve this, we'll need do some more research on how to make the colour sensor detect colour and then continue testing this out.


**Working Towards:**
- Researching out how to make the colour sensor detect green and blue.
- Changing the code to fit the original program plan once we identify and fix the issue (with the colour sensor).
---
```
# TEST 3
# Play a beep sound to signal the program has started
ev3.speaker.beep()


# The robot drives continuously unless there's a break in the loop
while True:
   colour = colour_sensor.color()
   robot.drive(200, 0)


    #if obstacle_sensor.distance() < 300:
      #wait(3)
    # If the colour sensor detects blue, beep twice then break the while loop
   if colour == Color.BLUE:
      ev3.speaker.beep()
      ev3.speaker.beep()
      break
    # If the colour sensor detects green, beep three times then break the while loop
   if colour == Color.GREEN:
      ev3.speaker.beep()
      ev3.speaker.beep()
      ev3.speaker.beep()
      break
   #else:
      #ev3.speaker.beep()
      #break
```
After Mr Scott helped us, the colour sensor started working. Actaully, the problem wasn't entirely our code's fault. By isolating the code that detects the colour and working with that, he found that the colour sensor on our EV3 robot detected light rather than colour, which is why our code wouldn't work.


With his help, we can start working on adapting this code into our program so the robot can evade blue and green obstacles.


**Working Towards:**
- Changing the code to fit a ~~original~~ new program plan.


> #### Evaluate your process in solving this test case.
> Overall, I think we were very successful in meeting this test case's requirements as with this test case alone, the robot does avoids the obstacles. However, this test case was not in our final program as it was unnecessary in our new plan because we had to change the way our robot goes around the path. 

>Some challenges we faced for this test case was with the colour sensor, which we were able to identify it's issue by isolating the colour sensor's function. We found out that the way we coded it made the code break too early in the while code, and also that our robot's settings for the colour sensor was light instead of colour. I think the robot detecting the obstacle using the ultrasonic sensor and just avoiding it alone went really well, but I believe that this test case could be improved next time particularly around the colour sensor's function.


### 3. Red/Yellow Obstacle Capture + Return Path after Capture (conjoined)


| Input | Process | Output|
|---------- |---------- |----------------   |
| Ultrasonic sensor detects obstacle within 10 cm distance | Robot pauses, moves forward 10-20cm and turns 180 degrees and drives back to the start area (corresponding to red and yellow) | Robot captures red/yellow obstacle within its 'arms' and takes it back to the start area


```
# TEST 1
collected_obstacles = 0


# Play a beep sound to signal the program has started
ev3.speaker.beep()


while collected_obstacles < 2:
  colour = colour_sensor.color()
  robot.drive(200, 0)




  if obstacle_sensor.distance() < 300:
      wait(3)
      if colour == Color.YELLOW:
         robot.straight(100)
         robot.turn(225)
         robot.straight(200)
         robot.turn(140)
         robot.straight(120)
         robot.straight(-30)
         collected_obstacles += 1
```
After testing the robot capturing the yellow, we realised that our colour sensor can't detect the colour from the way we were trying to go as one of the obstacles are in the way. Because of this, we have to scratch our original plan (and probably the obstacle evasion) and start first by collecting the red obstacle from the left, then the yellow. We also found out that the robot doesn't turn 180 or 90 degrees accurately on the sheet (maybe because of the texture??) so this is going to require more testing and time.


**Working Towards:**
- Getting the robot accurately to the red obstacle (QUICKLY!!)
- Creating the robot's arms so we can afterward start tesing out the robot capturing the red obstacle (by turning 180)
---
```
# TEST 2
# Display ":3" and play a beep sound to signal the program has started
ev3.screen.draw_text(40, 50, ":3")
ev3.speaker.beep()


# The robot drives up so its facing the red obstacle
robot.straight(200)
robot.turn(107)
robot.straight(595)
robot.turn(107)


while True:
   # Robot autodrives using the while code
   robot.drive(50, 0)
   # Once it detects an obstacle within 10 cm
   if obstacle_sensor.distance() < 100:
      wait(2)
      # The robot's screen displays "Obstacle Detected! :0"
      ev3.screen.clear()
      ev3.screen.draw_text(40, 50, "Obstacle Detected! :0")
      break


# If that obstacle is red
if colour_sensor.color() == Color.BLUE:
   # The robot's screen displays "RED Detected! :3"
   ev3.screen.clear()
   ev3.screen.draw_text(40, 50, "RED Detected! :3")
   robot.straight(100)
   robot.turn(196)
   wait(3)      
```      
It goes up to the red obstacle (we had to substitute it for a blue one at the time) and starts auto-driving and checking for an obstacle. For some reason its not really stopping so we're not sure if it's detecting the obstacle, so we'll mainly be working on it detecting the obstacle and colour next lesson while still tweaking the robot going up to the obstacle. I'm glad we put the screen displays in as it adds a bit of like structure to the code and makes it easier to see which code is for which function.


Yuna also made the arms for us today! We had to adjust it so one of the arms is on the outside of the colour sensor so it when it detects a yellow or red obstacle, it can go straight forward and actually get it inside its arms. It's really stable and awesome so I'm hoping it won't need any tweaks later on.


**Working Towards:**
- Further refining the robot's pathway to the red obstacle so it can accurately detect
- Fixing the code so the robot detects the obstacle and stops
- Getting up to testing if the colour sensor is actually working
---
```
# TEST 3
# Beep to signal the program has started
ev3.speaker.beep()


# The robot drives up so its facing the red obstacle
robot.straight(200)
robot.turn(107)
robot.straight(595)
robot.turn(107)


while True:
   # Robot autodrives using the while code
   robot.drive(50, 0)
   # Once it detects an obstacle within 10 cm
   if obstacle_sensor.distance() < 100:
      robot.stop()
      # Its screen displays "Obstacle Detected! :0"
      ev3.screen.clear()
      ev3.screen.draw_text(40, 50, "Obstacle Detected! :0")
      break


# If that obstacle is red
if colour_sensor.color() == Color.RED:
   # Its screen displays "RED Detected! :3"
   ev3.screen.clear()
   ev3.screen.draw_text(40, 50, "RED Detected! :3")
   robot.straight(120)
   robot.turn(196)    
   # Robot going back to start area
   robot.straight(200)
   robot.turn(-107)
   robot.straight(595)
   robot.turn(-107)
   robot.straight(200)


# The robot drives up so its facing the yellow obstacle
robot.straight(200)
robot.turn(107)
robot.straight(670)
robot.turn(107)
robot.straight(450)
robot.turn(107)


while True:
   # Robot autodrives using the while code
   robot.drive(50, 0)
   # Once it detects an obstacle within 10 cm
   if obstacle_sensor.distance() < 100:
      robot.stop()
      # Its screen displays "Obstacle Detected! :0"
      ev3.screen.clear()
      ev3.screen.draw_text(40, 50, "Obstacle Detected! :0")
      break


# If that obstacle is yellow
if colour_sensor.color() == Color.YELLOW:
   # Its screen displays "YELLOW Detected! :3"
   ev3.screen.clear()
   ev3.screen.draw_text(40, 50, "YELLOW Detected! :3")
   # Robot going back to start area
   robot.straight(500)
   robot.turn(-107)
   robot.straight(200)
```
Today our robot didn't run any of the code even when we pressed it. This was similar to something that happened last time and we received help from Mr Scott for that but we don't remember what he did or said to fix it, and he is away in Tasmania.


Were not really sure how to fix it and we've done some research on how to find what the problem is but we only have two lessons left, which will probably be less than 2 hours since the other class keeps altering our robot, which takes up at least 10-15 minutes of our time. We're thinking instead of connecting and downloading this file to RickMan, we should create a separate one with just the 'main.py' in case its a problem with something in this project.


Sitting there idly not knowing what to do would've been a waste of time, so Arisa and I created the mock code for the entire program, which is what the code will supposedly look like, with a lot of approximate measurements for the 'robot.straight' and 'robot.turn' as RickMan doesn't turn 90 degrees when you code it to turn 90 degrees (perhaps due to the texture of the surface??). Next lesson, we'll try test it again separate to this project, and if that doesn't work, we'll try receive help from Mr Groom if he's next door. If we can get the code to work, we'll tweak all the approximate measurements and make it more accurate.


(once we get up to editing the robot going home, the testing will be moved to the next test case below)


**Working Towards:**
- Getting the stupid robot to run the code.
- Tweaking approximate measurements in the mock code so it's accurate.
- Testing if the ultrasonic and colour sensor are actually working.
---
```
# TEST 4
# Beep to signal the program has started
ev3.speaker.beep()


# The robot drives up so it's facing the red obstacle
robot.straight(200)
robot.turn(107)
robot.straight(595)
robot.turn(107)


while True:
   # Robot auto drives by driving 5 cm at a time while checking the if the if statement is true
   robot.drive(50, 0)
   # Once it detects an obstacle within 10 cm
   if obstacle_sensor.distance() < 100:
      robot.stop()
      # Its screen displays "Obstacle Detected! :0"
      ev3.screen.clear()
      ev3.screen.draw_text(20, 50, "Obstacle Detected!")
      # Robot moves forward 12 cm and turns back to capture obstacle
      robot.straight(120)
      robot.turn(196)    
      # Robot going back to start area
      robot.straight(200)
      robot.turn(-107)
      robot.straight(595)
      robot.turn(-107)
      robot.straight(200)
      break


# The robot drives up so it's facing the yellow obstacle
robot.straight(200)
robot.turn(107)
robot.straight(670)
robot.turn(107)
robot.straight(450)
robot.turn(107)


while True:
   # Robot auto drives by driving 5 cm at a time while checking the if the if statement is true
   robot.drive(50, 0)
   # Once it detects an obstacle within 10 cm
   if obstacle_sensor.distance() < 100:
      robot.stop()
      if colour_sensor.color()  == 6:  # Colour sensor detects the floor is white
        ev3.screen_clear()
        # The robot's screen displays that the floor is white (non-functional)
        ev3.screen.draw_text(20, 50, "w w waitt.. the floor MIGHT be white. heh.")
        wait(3000)
      # The robot's screen displays "Obstacle Detected!"
      ev3.screen.clear()
      ev3.screen.draw_text(20, 50, "Obstacle Detected!")
      # Robot going back to start area
      robot.straight(500)
      robot.turn(-107)
      robot.straight(200)
     
```
We separated the 'main.py' from this project and made a new github repository and the code now runs! We tweaked the measurements for the robot going to the red obstacle and coming back but it varies for some reason because it moves a bit differently each time. We only have one lesson left to tweak and also record our video so we'll be capturing the yellow obstacle and possibly sacrificing the colour sensor if the new (non-functional) code we wrote for it doesn't work.


 **Working Towards:**
- Tweaking approximate measurements in the mock code so it's accurate.
- Testing if the new colour sensor code wil work.
---
```
# TEST 5
# <-------------------------------------- FUNCTIONS -------------------------------------->


"""Function to include the two sensors
Use when the obstacle is right in line of path of the EV3 so it can stop by detecting the obstacle using the ultrasonic sensor.
Also incorporates the colour sensor in a really useless way just so it fits assessment requirements"""
def autodrive():
   
   while True:
       # Robot auto drives by driving 5 cm at a time while checking the if the if statement is true
      robot.drive(50, 0)
       # Once it detects an obstacle within 10 cm
      if obstacle_sensor.distance() < 100:
         robot.stop()
         if colour_sensor.reflection() > 50: # Colour sensor detects the floor is white (white reflects around 60-100 but the sheet is kind of off-white )
            ev3.screen.clear()
            # The robot's screen displays that the floor is white (non-functional)
            ev3.screen.draw_text(20, 50, "w w waitt.. the floor MIGHT be white. heh.")
            wait(3000)
         # The robot's screen displays "Obstacle Detected!""
         ev3.screen.clear()
         ev3.screen.draw_text(20, 50, "Obstacle Detected!")


"""Function for simplifying the main program so the "robot.straight()" and "robot.turn" don't make huge code blocks
Measurements of each robot.straight and robot.turn are added in the main program (when there's too many straights and turns, writing 0 just makes it do nothing)"""
def move_path(forward1, turn1, forward2, turn2, forward3, turn3):
   robot.straight(forward1)
   robot.turn(turn1)
   robot.straight(forward2)
   robot.turn(turn2)
   robot.straight(forward3)
   robot.turn(turn3)


# <-------------------------------------- PROGRAM -------------------------------------->


# Beep to signal the program has started
ev3.speaker.beep()


# The robot drives up so it's facing the red obstacle
move_path(200, 107, 595, 107, 0, 0)


# Robot drives forward (toward red block) until the ultrasonic sensor detects it within 10 cm
autodrive()


# Robot moves forward 12 cm and turns back to capture obstacle
move_path(120, 196, 0, 0, 0, 0)


# Robot going back to start area
move_path(200, -90, 595, -107, 200, 0)


# The robot drives up so it's facing the yellow obstacle
move_path(200, 107, 670, 107, 450, 107)


# Robot drives forward (toward yellow block) until the ultrasonic sensor detects it within 10 cm
autodrive()


# Robot going back to start area
move_path(500, -107, 200, 0, 0, 0)

```
We restructured the program so it uses two functions so its a bit more similar to my flowcharts and pseudocode (its also easier for me to figure out where to tweak). Tomorrow is our last lesson so we really need to tweak all the measurements so everything gets back home without going off the map or bumping into obstacles so that will be our main goal.


**Working Towards:**
- Tweaking approximate measurements in the mock code so it's accurate.
- Testing if the new colour sensor REFLECTION code wil work.
---
(Note from final class day 16/05/25)


**THE CODE WON'T RUN!!!** The robot keeps saying the code is not executable, but there's no problems with the code itself and the robot won't update the files even when we download it multiple times. We even asked Mr Groom for help but he said he didn't know and to just give up (he helped us for around 30 minutes). He also said wait until Monday and he said the robot was malfunctioning (apparently multiple robots too). Due to this, we won't be able to record our program in time but we have the code, although we didn't get to do any testing so it actually runs well.


> #### Evaluate your process in solving this test case.
> I think we were (sort of?) successful in meeting the test case requirements as we were able to incorporate the ultrasonic sensor (though not the colour sensor), which allowed our code to still follow the test case's input, process and output format. The obstacle sensor went especially well and needed virtually no tweaks, however the colour sensor presented a lot of challenges as it wasn't very accurate in detecting colours unless it was right up in front of it. Although we identified the errors with the colour sensor, such as it being too far away or our code being adjusted so the obstacle was in front of the ultrasonic sensor, ultimately I think we made the right decision to scratch our original plan for the colour sensor and make its use more accessory. I think some areas of improvement could've definitely been made, but we made good progress and did everything we could within the time span.

### Peer Evaluation Scaffold
>#### Arisa
>When rating 1-5 with 1 being lackluster effort and 5 being outstanding effort, how much effort do you feel this group member put into this project?

5/5

>Explain the reason for this score in detail:
Arisa but in outstanding effort into this project. She made sure that everyone knew what they were doing, that everything was done on time and to quality. She also discussed the project out of classes with me, and went with me to the computer classrooms at lunch to test our robot. She also did a lot of research at home in order to come prepared for the next lesson.


>When rating 1-5 with 1 being not at all and 5 being an exceptional amount, how much did this team member contribute to the team's efforts throughout this project?

5/5

>Explain the reason for this score in detail:

Arisa participated and contributed an exceptional amount, writing and doing as much as she could in time time span. She always encouraged us to do more, and helped me and Yuna in the research task by explaining things we didnt understand and making sure that everything gets done. She was also the person who wrote all of the code, while discussing with us what we did in each lesson what we did and should do next. Arisa was also the one to finish Yuna's research task questions while she was in Tasmania so nothing was left unfinished.


>When rating 1-5 with 1 being not well at all and 5 being exceptionally well, how well do you think this team member performed throughout all stages of the project?

4.9/5

>Explain the reason for this score in detail:

Overall, Arisa did exceptionally well in this project throughout all stages of the project. She made classes fun by keeping us engaged with her silly jokes about how stupid the robot was, and kept me and Yuna involved, even when we didn't know what was going on. She helped us stay quick on our feet so we didnt have to cram everything into one lesson at the end, and checked in on the research task at home to make notes and suggestions for our questions. (but then sometimes if she didnt think something was good enough she got a little scary and wrote it on her instagram status)


>#### Yuna
>When rating 1-5 with 1 being lackluster effort and 5 being outstanding effort, how much effort do you feel this group member put into this project?

4.5/5

>Explain the reason for this score in detail:

Yuna put a lot of effort into the project, since she was consistenly on task and helping us whenever she could. She contributed thoughtgully in group discussions and took initiative in the building component for the task. She showed strong commitment through every lesson and kept the group organised and on track, but there would be times where she would just zone out and sit there aimlessly.

>When rating 1-5 with 1 being not at all and 5 being an exceptional amount, how much did this team member contribute to the team's efforts throughout this project?

3.5/5

>Explain the reason for this score in detail:

Yuna made the arms for the robot (which me and Arisa had to rebuild later on, but it was essential for the early stages) and participated to her fullest, however, for the research task, she wasn't able to write enough for each question. Despite this, she was very aware of the deadlines and completed things early, however, she went on holiday at the same time as Mr. Scott, so she wasn't able to participate when we were cramming the final run. It would have been better if Yuna provided more detail for this, but overall, she did well in contributing to the projects.

>When rating 1-5 with 1 being not well at all and 5 being exceptionally well, how well do you think this team member performed throughout all stages of the project?

3.9/5

>Explain the reason for this score in detail:
Yuna performed well across most stages of the project. She was almost always engaged and her construction of of the robots arms was fundamental for our project development, even if we did have to rebuild them later. However, her lack of detail in the written research task and absence during the final stages of the task limited her overall involvement. Regardless, her consistent effort and teamwork made her a overall a valuable member.

### Final evaluation questions

>Evaluate your GROUP'S Final Performance in Relation to the Identified Need
#### Identified need: Transport the red and yellow blocks using colour and touch sensor, while avoiding the rest of the obstacles.

Our robot could not run our final performance due to malfunction, however, when we were working on it before, the robot could transport the red block back to the station almost flawlessly and the yellow block near the station with minor issues. (It would sometimes touch the other obstacles or run off the mat)


>Evaluate your Project in Relation to Project Management

Our project management was handled resonably well. Although we were not able to film our final video because of the robot not working, we pretty much finished everything else. However, some stages of the project were slightly rushed at then end, so improved time allocation could have helped last minute pressure. 

>Evaluate your Project in Relation to Team Collaboration

Each member in our team contributed to their share of work, and we communicated regularly to solve issues and research together. While Arisa was more consistent in contributions (me and Yuna were both away for a week), overall, everyone was cooperative and supportive, eager to get work done. 

>Justify Future Improvements you could make to your Final Product

It would be nice if we were able to see our final product, as the robot started malfunctioning during the final stages, which prevented us from running the code and seeing our robot in action. However, before this, we were having trouble getting the colour sensor to work, and the right angles and measurements, so maybe we could have improved that if we had no technical difficulties. 
