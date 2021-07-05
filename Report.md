# Report

## implementation

### environment details
For any reinforcement learning implementation, the agent has to interact with their environment. In this case, the environment space is represented by 33 different variables that incorporate position, rotation, velocity, and the arm's angular velocity.

### rewards
The agent's goal is to maintain the arm in the target area for as long as possible (as measured by time steps). As such the agent recieves a reward of +.1 for each time step that the arm is in the target area.

### state space
The state space has to total of 37 dimensions and keeps information on the velocity of the agent, as well a ray based perception of objects in front of the agent.

### action space
Within the environment, there is a discrete action space of 4. 
Per the udacity program the agent able to take action represented by four numbers that correspond to the torque of the arm's two joints. 

### task success
In order to successfully complete the episodic task, the agent is required to obtain an average score of 30 or above over the course 100 episodes.

## algorithm

### DDPG
To train this agent, I utilized the DDPG algorithm. DDPG is an actor-critic method. DDPG is known as an off-policy algorithm and is very similar to the DQN with some differences. Different from the DQN, DDPGs are able to solve tasks in a continuous action space.

DDPG also uses four different neural networks; rather than just an actor and a critic, this algorithm uses what is called a local actor as well as a target actor, and similarly for the agent; a local agent and a target agent.

### hyper-parameters

- replay buffer size: 1e6
- max timesteps: 3000 (all episodes get shutdown after 3000 timesteps)
- minibatch size: 256
- discount factor: 0.99
- tau (soft update for target networks factor): 1e-3
- learning rate: 1e-4 (actor) and 1e-3 (critic)
- update interval (how often to learn): 2
- beta start (factor for the noise added to the actions selected by the actor): 0.1
- beta decay factor: 0.995
- min beta: 0.01

I tuned the above parameters manually and randomly. It didn't take too long before I was successfully solving the environment. 

### model architecture
Because of the state space, my neural network takes a 33 by 1 vector from the environment. My output layer includes 4 outputs, 1 corresponding to each action in the action space. There are also 64 nodes in each of the two hidden layers.

## plot & performance
![image](https://user-images.githubusercontent.com/13371867/123744365-e5985c80-d86b-11eb-9c00-0676df93dc08.png)
- Episode 100	Average Score: 12.19
- Episode 108	Average Score: 13.02
- Environment solved in 108 episodes!	Average Score: 13.02

## improvements

- My hyper-parameter was largely a manual implementation of random search. Random can be ok, if somewhat controlled in a systematic fashion. I would have preferred to implement grid search or random search to determine hyper parameters in the end.

- Rather than just going with the DDPG, I would like to test each of the reviewed actor critic methods: PPO, A3C, or D4PG
