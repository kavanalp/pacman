# pacman

1. Introduction

In the Reinforcement learning world, the purpose is to build a pipeline in which machines or agents are able to learn how to act in different circumstances to get the greatest results they can.
One of the most popular problems in RL is the Pacman game in which an agent or agents can learn how to get to the food as fast as possible without being harmed by other agents(or ghosts) in the game. 

2. Problem description 
Our problem is very similar to the Pacman game with any obstacles and infinite 
sequences of actions which the purpose is to get to the maximum sum of rewards

2.1 Environment
We have a greedy 20*20 space with 4 agents and 8 foods located in this space

2.2 Actions
Every agent can make move and attack towards four cardinal directions(N, S, W, E)

2.3 Rewards
Through every action we assign a reward based on the actions done by an agent as follows:
We assign value 1 for moving toward a food position
We assign value 2 for attracting correctly toward another agent
We assign value -4 for an agent being attacked by another 
We assign value -0.01 for an unsuccessful attack done by an agent
We assign 0 for any other actions


3. Purpose
We want to learn this agent to get to do their best action in final exploitation

4. Exploration
In every iteration, the agent chooses an action with respect to the value of epsilon(shows how random should agent act) and the experience it has with the following types:

4.1.Decreasing Epsilon:
 In this part, we assign an initial value that decreases based on the defined exploration which is reduced during expiration till it becomes 0.
In this type, the agent acts totally random and the first few iterations and step by step the epsilon becomes smaller till we get to 0 and the agent chooses the best action that receives the maximum reward if available.

4.2 Constant Epsilon:
In this part, the agent chose an action totally random and after a defined exploration number, the agent chooses an action based on the constant epsilon which is near to 0, between the action that gets the maximum reward and random action.

5. Space complexity 
We study the space complexity of the environment and an agent viewing angle

5.1 Environment
An environment has 4 agents 8 foods  and 388 empty spaces
C(12, 400)*C(4,12)*C(8, 8)
%

5.2 Agent
An agent can see 8 surrounding spaces which could be food, another agent, or empty space. This consist of 8 empty space 3 agents and 8 foods
C(8,19) = 75000
And every 8 action it will be 600,000 states

6 Exploitation
After agents get to this step they start choosing the best action based on the experiences they receive to get to the maximum reward of every single step.
Epsilon in 0 in this part

7. Results
We will try different input parameters and see what’s happening by showing learning plots


7.1 Epsilon 
How random should we act

7.1.1 Decreasing
If we apply this at every step probability of choosing random action by an agent 
reduces by iteration. This would be a great choice to have a greater cumulative reward even during learning.

7.1.2 Constant
Else the agent chooses totally random actions and after a large number of iterations
(when start exploiting) the agent chooses the best action wisely based on the value of epsilon which is near to 0. It takes less time and the cumulative reward is not good compared to decreasing one. 

7.1.3 Conclusion
At last if after exploring we initialize agents in the environment again it's better to choose constant epsilon because it may have more experience. If the exploiting exactly starts after exploring it is better to choose decreasing epsilon


8. Iteration
How many iterations should we choose to explore and exploit

8.1 Exploration
As considered spending more iteration on exploring gives us better value
I started with 2000 iterations which learned approximately random(from 4 agents 2 of them learned) with 5000 iterations slightly better than 2000 and in 10000 iteration 
4 agents were learned completely as well in 20000

2000 iterations take on average 30 seconds to be done



5000 iterations take on average 140 seconds to be done


10000 iterations take on average 540  seconds to be done

20000 iterations take on average 2100 seconds to be done



*You can see my full plots from this link 
We can see iteration takes O(2,n) which n is the number of iteration
For example, if we do this for 75000(all combinations of states) iteration is equal to 7.5 * time of 20000 which is 2100 seconds so it takes about 4 hours and a half.


8.2 Exploitation
I regularly choose 0.1 of exploration because it does not affect learning but cumulative reward. If exploitation is too much, if the agent converges in doing best action its cumulative reward increases highly but we should notice the agent is not converged we get very bad results and vice versa for very small exploitation.

9. Discount factor
I pickled 0.9 as a discount factor for checking 2 sequences of actions to get to the maximum sum of rewards. The first reward is added to 0.9 multiplied by the second reward. This let us do the best action as fast as possible


https://colab.research.google.com/drive/1-zjXShXrCiC34MqTAwoyexjnhHxBNHVw



