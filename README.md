# M_DRL
NTB elective module for Deep Reinforcement Learning<br>
To obtain the credits for the module Deep Reinforcement Learning, students are required to implement two small projects:
- Miniproject 1: Classic Tabular Reinforcement Learning
- Miniproject 2: Deep Reinforcement Learning with ray

## Miniproject 1: Cliff Walking
This is a standard un-discounted, episodic task, with start and goal states, and the usual actions causing
movement up, down, right, and left. Reward is -1 on all transitions except those into the region marked
Cliff. Stepping into this region incurs a reward of optimal path -100 and sends the agent instantly back to
the start.

See my solution in this [Jupyter Notebook](https://github.com/alkolhar/M_DRL/blob/main/MiniProject-Cliff_Walking.ipynb)

![Cliff Walking](/images/cliff_walking.png)

### SARSA algorithm
![SARSA algorithm](/images/sarsa-algorithm.png)<br>
State–action–reward–state–action (SARSA) is an algorithm for learning a Markov decision process policy.
This name simply reflects the fact that the main function for updating the Q-value depends on the current state of the
agent "S1", the action the agent chooses "A1", the reward "R" the agent gets for choosing this action, the state "S2"
that the agent enters after taking that action, and finally the next action "A2" the agent chooses in its new state. 

#### Resulting Q-Table
![Q-Table Sarsa](/images/q-table-sarsa.png)<br>
This table shows the Q values for everey state in the game. Every state has a Q value for every action in 
that state. This value represents the expected future reward on the given action. Eye-catching is the fact
that in one state the different values for an action are just slightly different.

### Q-Learning algorithm
![Q-Learning algorithm](/images/q-algorithm.png)<br>
The Q-Learning algorithm differs only slightly from SARSA. It also calulates the Q values from state-action paris,
but the next action does not come from a greedy policy, instead the highest possible value is chosen.

#### Resulting Q-Table
![Q-Table Sarsa](/images/q-table-q_learning.png)<br>
If this Q value table is compared with the same table when applying the SARSA algorithm the main difference
is that in this table, the values in one state are more distinct for the differenct actions, than in the
SARSA table.

### Problems and Limitations
With the SARSA algorithm the optimal path is found but it takes more episodes, and the Q values are not that 
clear to differ. This algorithm tends to take a longer but "safer" path.

Q- Learning instead learns values for the optimal policy, which travels right along the edge of the cliff.
Unfortunately, this results in its occasionally falling off the cliff because of the epsilon-greedy action
selection.

## Miniproject 2: Lunar Lander
Using reinforcement learning approaches, we want to tackle the lunar lander environment in the OpenAI gym kit.
The environment, which includes a well-defined physics engine, replicates a situation in which a lander must land at a precise point in low-gravity conditions.
The basic purpose of the game is to guide the agent as softly and efficiently as possible to the landing pad. The state space, like in real physics, is continuous, but the action space is discrete.

See my solution in this [Jupyter Notebook](https://github.com/alkolhar/M_DRL/blob/main/MiniProject-LunarLander.ipynb)<br>
<img src='https://github.com/alkolhar/M_DRL/blob/main/images/before-training.gif?raw=true' />
![before-training](https://github.com/alkolhar/M_DRL/blob/main/images/before-training.gif)<br>

### Environment
There are four discrete actions available: do nothing, fire left orientation engine, fire main engine, fire right orientation engine. There are 8 states: the coordinates of the lander in x & y, its linear velocities in x & y, its angle, its angular velocity, and two Booleans that represent whether each leg is in contact with the ground or not.
Reward for moving from the top of the screen to the landing pad and coming to rest is about 100-140 points. If the lander moves away from the landing pad, it loses reward. If the lander crashes, it receives an additional -100 points. If it comes to rest, it receives an additional +100 points. Each leg with ground contact is +10 points. Firing the main and side engines is -0.3 points for each frame. Solved is 200 points. The lander starts at the top centre of the viewport with a random initial force applied to its centre of mass.
The episode finishes if the lander has crashed, or the lander gets outside of the viewport.
1.	The lander has crashed
2.	The lander gets outside of the viewport

### Deep Q Network
Deep Q Networks are used, in order to easily scale Table Q Learning-based algorithms by replacing them with a neural network, able to learn how to correctly estimate the Q Values (Function Approximation).

#### Hyperparameter tuning
![HyperTuning](/images/hyperparameter-tuning.png)<br>
To optimize our Agent, we decided to run some hyperparameter tuning first. We run a grid search on the number of hidden layers and the activation function in the fully connected network.
Due to the lack of proper computing power, the search for optimal learning rate is done after the first tuning.
The best configuration ran with 512 layers, a linear activation function and a learning rate of 0.0001. The result of this agent is visualized in the sections below.

### Episodes needed
![Episodes](/images/episodes.png)<br>
The gradient of the steps – episodes plot is quite steep at the start of training.
This means that the lander did not take many steps/actions until it crashed or landed, probably because of the first one. Then after about 500 episodes the lander learned presumably how to land, because after that it takes more steps until an episode is finished.
At the end of training the steps begin to decline again but the reason this time is that the lander now is landing efficiently in the zone.<br>
![after-training](https://github.com/alkolhar/M_DRL/blob/main/images/after-training.gif)

