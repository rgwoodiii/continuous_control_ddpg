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

- n_episodes = 1000 #episode volume
- max_t = 1000 
- print_every = 10 # output update frequency

- BUFFER_SIZE = int(1e5)  # replay buffer size
- BATCH_SIZE = 128        # minibatch size
- GAMMA = 0.99            # discount factor
- TAU = 1e-3              # for soft update of target parameters
- LR_ACTOR = 1e-4         # learning rate of the actor 
- LR_CRITIC = 1e-3        # learning rate of the critic
- WEIGHT_DECAY = 0        # L2 weight decay

I tuned the above parameters manually. It didn't take too long before I was successfully solving the environment. That said, the running of this model takes a super long time, so there wasn't an insane volume of iteration.

### model architecture
Because of the state space, my neural network takes a 33 by 1 vector from the environment. My output layer includes 4 outputs corresponding of values between -1 and 1 for each of the four actions in the action space. 

## plot & performance
![image](https://user-images.githubusercontent.com/13371867/123744365-e5985c80-d86b-11eb-9c00-0676df93dc08.png)
- Episode 100	Average Score: 12.19
- Episode 108	Average Score: 13.02
- Environment solved in 108 episodes!	Average Score: 13.02

## improvements

- My hyper-parameter was largely a manual implementation of random search. Random can be ok, if somewhat controlled in a systematic fashion. I would have preferred to implement grid search or random search to determine hyper parameters in the end.

- Rather than just going with the DDPG, I would like to test each of the reviewed actor critic methods: PPO, A3C, or D4PG
