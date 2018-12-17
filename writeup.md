# Deep RL Arm Manipulation

Seongyoon Cho

## Reward Functions

#### Reward Constants

The constants for winning and losing rewards are defined like these. 
```
REWARD_WIN = 2000.0f
REWARD_LOSS = -2000.0f
```

#### Goal Reward
`reward = REWARD_WIN`

If the robot achieves the goal, `REWARD_WIN` is issued and the episode ends. This value is set to a relatively high to give a significant amount of reward compared to **interim reward** introduced later. The reward is the same for both tasks, a task for any part of a robot arm touches the object, and the other task for gripper base touches the object. 

#### Reward for Touching the Ground
`reward = REWARD_LOSS * distGoal`

If the gripper base touches the ground, a negative reward is issued, and the episode ends. This value is multiplied by a distance between the gripper and the target object. i.e., if the gripper touches the ground far from the target object, a more significant negative value is issued. If the gripper just slightly misses the target object and hit the ground, a small negative value is issued.

#### Interim Reward
`avgGoalDelta  = (avgGoalDelta * alpha) + (distDelta * (1.0f - alpha))`

While the robot is in motion, an interim reward is issued to encourage robot to move towards to the target. The reward is smoothed with an alpha value of 0.2.

#### Joint Control
Both velocity control and position control is implemented for this project. But only position control made a promising result. Velocity control shows smoother movements but somehow failed to achieve over 0.7 of accuracy for task 2.

## Hyperparameters

## Results

## Future Works

