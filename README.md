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

![Cliff Walking](/images/cliff_walking.png)

### Specifications
- [x] Pick one of the simple, classic textbook RL problems
- [x] Separate the environment from the agent
- [x] Implement the SARSA algorithm
- [ ] \(Optional) Implement the SARSA-λ algorithm
- [x] Use the epsilon-greedy policy
- [ ] \(Alternative) Search for softmax policy with temperature τ
- [ ] Visualize and discuss your observations in the report

### SARSA algorithm
![SARSA algorithm](/images/sarsa-algorithm.png)

State–action–reward–state–action (SARSA) is an algorithm for learning a Markov decision process policy.
This name simply reflects the fact that the main function for updating the Q-value depends on the current state of the agent "S1", the action the agent chooses "A1", the reward "R" the agent gets for choosing this action, the state "S2" that the agent enters after taking that action, and finally the next action "A2" the agent chooses in its new state. 


## Miniproject 2: TBD.
