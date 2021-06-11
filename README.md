# AI 인공지능
See Midterm and Final Project:
https://sites.google.com/hanyang.ac.kr/2021ai

## Environment / Dependencies
```bash
Windows 10
Anaconda 4.10.1
Python 2.7
```

## Getting Started

* Files you'll edit:
```bash
valueIterationAgents.py		A value iteration agent for solving known MDPs.
qlearningAgents.py			Q-learning agents for Gridworld and Pacman.
```

* Files you should read but NOT edit:
```bash
mdp.py						Defines methods on general MDPs.
learningAgents.py			Defines the base classes ValueEstimationAgent and QLearningAgent, which your agents will extend.
util.py						Utilities, including util.Counter, which is particularly useful for Q-learners.
gridworld.py				The Gridworld implementation.
featureExtractors.py		Classes for extracting features on (state,action) pairs. Used for the approximate Q-learning agent (in qlearningAgents.py).
```

To get started, run Gridworld in manual control mode, which uses the arrow keys:
```bash
python gridworld.py -m
```
You will see the two-exit layout from class. The blue dot is the agent. Note that when you press up, the agent only actually moves north 80% of the time. Such is the life of a Gridworld agent!

You can control many aspects of the simulation. A full list of options is available by running:
```bash
python gridworld.py -h
```

The default agent moves randomly
```bash
python gridworld.py -g MazeGrid
```
You should see the random agent bounce around the grid until it happens upon an exit. Not the finest hour for an AI agent.

##Task1: MDP and Value Iteration
Write a value iteration agent in ValueIterationAgent, which has been partially specified for you in valueIterationAgents.py. 

On the default BookGrid, running value iteration for 5 iterations should give you this output:
```bash
python gridworld.py -a value -i 5
```
![Hint img1](imgs/task1_img.jpg)

## Task2: Q-Learning
write a Q-learning agent. A stub of a Q-learner is specified in QLearningAgent in qlearningAgents.py.(must implement the update, computeValueFromQValues, getQValue, and computeActionFromQValues methods.)

With the Q-learning update in place, you can watch your Q-learner learn under manual control, using the keyboard:
```bash
python gridworld.py -a q -k 5 -m
```
If you manually steer Pacman north and then east along the optimal path for four episodes, you should see the following Q-values:
![Hint img2](imgs/task2_img.jpg)

## Task3: Q-Learning for Pacman
Test games are shown in the GUI by default. Without any code changes you should be able to run Q-learning Pacman for very tiny grids as follows:
```bash
python2.7 pacman.py -p PacmanQAgent -x 2000 -n 2010 -l smallGrid
```	
While a total of 2010 games will be played, the first 2000 games will not be displayed because of the option -x 2000, which designates the first 2000 games for training (no output). Thus, you will only see Pacman play the last 10 of these games. The number of training games is also passed to your agent as the option numTraining.
```bash
python2.7 pacman.py -p PacmanQAgent -n 10 -l smallGrid -a numTraining=10
```
During training, you will see output every 100 games with statistics about how Pacman is faring. Epsilon is positive during training, so Pacman will play poorly even after having learned a good policy: this is because he occasionally makes a random exploratory move into a ghost. As a benchmark, it should take between 1,000 and 1400 games before Pacman's rewards for a 100 episode segment becomes positive, reflecting that he's started winning more than losing. By the end of training, it should remain positive and be fairly high (between 100 and 350).