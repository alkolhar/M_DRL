# M_DRL
NTB elective module for Deep Reinforcement Learning<br>
To obtain the credits for the module Deep Reinforcement Learning, students are required to implement two small projects:
- Miniproject 1: Classic Tabular Reinforcement Learning
- Miniproject 2: Deep Reinforcement Learning

> :warning:	This is an ongoing project. This page does not reflect the current state. :warning: <br>
> To see the current status of the work, please visit my [GitHub DRL Repository](https://github.com/alkolhar/M_DRL/)

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

## Miniproject 2: TBD.
