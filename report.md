# Udacity Deep Reinforcement Learning 

## Navigation Project Executuve Summary

Author: Alva Presbitero avpresbitero@gmail.com

### Overview

In this project, I will go over Deep Q Networks (DQN), a known approach in Reinforcement Learning that utilized neural networks for learning states and actions that give out the best rewards. This project is part of the Udacity Deep Reinforcement Learning nanodegree course.

The environment that we will learn from today is the world of bananas. The project's goal is to train an agent in such a way that it collects only the yellow bananas and avoid the blue bananas.

The project environment is built in Unity, specifically the Banana Collector version. 

### The Environment

Again the goal of this project is to train an agent to navigate (and collect bananas!) in a large, square world.

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

 1. up
 2. down
 3. left
 3. right


### The Solution

The learning algorithm I picked for this project is a vanilla Deep Q-Learning algorithm, based on Deep Mind's paper entitled "Human Level Control Through Deep Reinforcement Learning" publisjed in Nature back in February 2015. 


### Model architecture

I ventured into the simpler/shallower network configurations as often times, simple algrorithms achieve the desired results without compromising computational power. Hence, in this project, a 2-layer neural network was used (2 linear or fully connected layers) with input 37 and output 4. The architecture makes use of 64 and 128 neurons respectively.

```
QNetwork(
  (fc1): Linear(in_features=37, out_features=64, bias=True)
  (fc2): Linear(in_features=64, out_features=128, bias=True)
  (out): Linear(in_features=128, out_features=4, bias=True)
)
```

### Hyperparameters

All hyper parameters were fixed during the testing. We had expected to need to "play" with these to optimise the solution, however, the training results were such that this was not needed. 

* Replay buffer size 100,000 
* Discount factor 0.99 (gamma)
* Soft update factor 0.001 (tau)
* Learning rate 0.0004 (alpha)
* Network update step interval 4

## Results

I was suprised by the results, specifically, how easy it was to achieve the goal score with almost no modifications. The consistent solving of the problem when training, and the low number of episodes required, was not expected. 

We had expected to spend significant time tuning hyperparams and running on GPU instances, however, our MacBook Pro CPU completed the training in under 5 minutes.

![raw scores](raw_scores_dqn.jpg)

![average scores](average_scores_dqn.jpg)


```
Episode 100	Average Score: 1.02
Episode 200	Average Score: 3.88
Episode 300	Average Score: 6.90
Episode 400	Average Score: 9.46
Episode 500	Average Score: 12.33
Episode 522	Average Score: 13.02
Environment solved in 422 episodes!	Average Score: 13.02
```

## Conclusion and Recommendations

Solving the task only required a shallow architecture as a task as simple as this would not require more complicated algorithms. However, Dueling DQN, Rainbow and other more advance implementations are still worth exploring as I have noticed that increasing the episodes did not do much to the learning. Maybe other approaches may also be explored other than the Epsilon Greedy approach. 


