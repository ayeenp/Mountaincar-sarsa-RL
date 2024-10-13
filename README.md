# Mountain Car Reinforcement Learning

This repository focuses on solving the Mountain Car problem using Q-Learning and SARSA algorithms.

## Overview

The Mountain Car problem is a classic reinforcement learning task where an underpowered car must drive up a steep hill. The car must learn to leverage potential energy by driving back and forth to reach the goal.

## Algorithms

- **Q-Learning**: Off-policy TD control algorithm.
- **SARSA**: On-policy TD control algorithm.

## Installation

Install the required libraries:
    
```bash
pip install numpy matplotlib gymnasium
```

## Usage

1. **Train the Q-Learning Agent**:
    ```python
    EPISODES = 10000
    LEARNING_RATE = 0.15
    DISCOUNT = 0.95
    EPSILON = 0.2
    DISCRETE_SIZE = 35

    mountain_car_ql = MountainCarQL(env, discrete_size=DISCRETE_SIZE)
    mountain_car_ql.learn(EPISODES, LEARNING_RATE, DISCOUNT, EPSILON)
    ```

2. **Evaluate the Q-Learning Agent**:
    ```python
    mountain_car_ql.create_policy()
    avg_score, win_percentage = mountain_car_ql.evaluate(500)
    print(f"Average Score: {avg_score}, Win Percentage: {win_percentage}")
    ```

3. **Train the SARSA Agent**:
    ```python
    mountain_car_sarsa = MountainCarSarsa(env, discrete_size=DISCRETE_SIZE)
    mountain_car_sarsa.learn(EPISODES, LEARNING_RATE, DISCOUNT, EPSILON)
    ```

4. **Evaluate the SARSA Agent**:
    ```python
    mountain_car_sarsa.create_policy()
    avg_score, win_percentage = mountain_car_sarsa.evaluate(500)
    print(f"Average Score: {avg_score}, Win Percentage: {win_percentage}")
    ```

## Visualization

Visualize the path taken by the car for one episode:
```python
env.reset()
visualize(env)
for i in range(200):
    reward, done = mountain_car_ql.act()
    if i % 10 == 0:
        visualize(env)
    if done:
        break
```

## Results
- Q-Learning: Higher win percentage and better average score.
- SARSA: Slightly lower performance compared to Q-Learning.