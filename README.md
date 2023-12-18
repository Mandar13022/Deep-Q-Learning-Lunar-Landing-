# Deep-Q-Learning-Lunar-Landing-

# Description:
This environment is a classic rocket trajectory optimization problem. According to Pontryagin’s maximum principle, it is optimal to fire the engine at full throttle or turn it off. This is the reason why this environment has discrete actions: engine on or off.
There are two environment versions: discrete or continuous. The landing pad is always at coordinates (0,0). The coordinates are the first two numbers in the state vector. Landing outside of the landing pad is possible. Fuel is infinite, so an agent can learn to fly and then land on its first attempt.

# Action Space
There are four discrete actions available:
0: do nothing
1: fire left orientation engine
2: fire main engine
3: fire right orientation engine

# Observation Space
The state is an 8-dimensional vector: the coordinates of the lander in x & y, its linear velocities in x & y, its angle, its angular velocity, and two booleans that represent whether each leg is in contact with the ground or not.

# Rewards
After every step a reward is granted. The total reward of an episode is the sum of the rewards for all the steps within that episode.
For each step, the reward:
1) is increased/decreased the closer/further the lander is to the landing pad.
2) is increased/decreased the slower/faster the lander is moving.
3) is decreased the more the lander is tilted (angle not horizontal).
4) is increased by 10 points for each leg that is in contact with the ground.
5) is decreased by 0.03 points each frame a side engine is firing.
6) is decreased by 0.3 points each frame the main engine is firing.

The episode receive an additional reward of -100 or +100 points for crashing or landing safely respectively.
An episode is considered a solution if it scores at least 200 points.

# Starting State
The lander starts at the top center of the viewport with a random initial force applied to its center of mass.

# Episode Termination
The episode finishes if:
the lander crashes (the lander body gets in contact with the moon);
the lander gets outside of the viewport (x coordinate is greater than 1);
the lander is not awake. From the Box2D docs, a body which is not awake is a body which doesn’t move and doesn’t collide with any other body
