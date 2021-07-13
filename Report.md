# Report

## implementation

### environment details
For any reinforcement learning implementation, the agent has to interact with their environment. In this case, the environment space is represented by 33 different variables that incorporate position, rotation, velocity, and the arm's angular velocity.

### rewards
The agent's goal is to maintain the arm in the target area for as long as possible (as measured by time steps). As such the agent recieves a reward of +.1 for each time step that the arm is in the target area.

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

- n_episodes=3000         # maximum number of episodes to train
- max_t=1000              # maximum number of steps to train per episode

- BUFFER_SIZE = int(1e6)  # replay buffer size
- BATCH_SIZE = 128        # minibatch size
- GAMMA = 0.99            # discount factor
- TAU = 1e-3              # for soft update of target parameters
- LR_ACTOR = 1e-4         # learning rate of the actor 
- LR_CRITIC = 1e-3        # learning rate of the critic
- WEIGHT_DECAY = 0        # L2 weight decay
- LEARN_EVERY = 20        # update the networks 10 times after every 20 timesteps
- LEARN_NUMBER = 10       # update the networks 10 times after every 20 timesteps
- EPSILON = 1.0           # noise factor
- EPSILON_DECAY = 0.99    # noise factor decay

I tuned the above parameters manually. This each run took a very long time, I had to run this on the udacity provided GPU as my personal machine struggled. Given the runtime, I didn't perform as much iteration as I would have preferred.

### model architecture

#### actor architecture
- input layer = 33
- fully connected hidden layer = 400 nodes, relu activation function
- fully connected hidden layer = 300 nodes, relu activation function
- output layer = 4, tanh activation function

#### critic architecture
- input layer = 33
- fully connected hidden layer = 400 nodes, relu activation function
- fully connected hidden layer = 300+4(+ actions) nodes, relu activation function
- output layer = 1

## plot & performance
![image](https://user-images.githubusercontent.com/13371867/125349077-4d45b180-e31a-11eb-9099-5ef91a17dab1.png)
- Episode 100 Average_Score: 1.74
- Episode 200 Average_Score: 4.96
- Episode 300 Average_Score: 7.33
- Episode 400 Average_Score: 7.06
- Episode 500 Average_Score: 9.63
- Episode 600 Average_Score: 11.45
- Episode 700 Average_Score: 14.32
- Episode 800 Average_Score: 15.82
- Episode 900 Average_Score: 17.76
- Episode 1000 Average_Score: 18.53
- Episode 1100 Average_Score: 21.97
- Episode 1200 Average_Score: 22.40
- Episode 1300 Average_Score: 23.30
- Episode 1400 Average_Score: 24.84
- Episode 1500 Average_Score: 28.03
- Episode 1600 Average_Score: 28.02
- Environment solved in 1551 episodes!	Average_Score: 30.02

## improvements

- My hyper-parameter was largely a manual implementation of random search. Random can be ok, if somewhat controlled in a systematic fashion. I would have preferred to implement grid search or random search to determine hyper parameters in the end.

- Rather than just going with the DDPG, I would like to test each of the reviewed actor critic methods: PPO, A3C, or D4PG
