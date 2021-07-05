# continuous_control_ddpg

As part of the Deep reinforcement learning nano degree with Udacity, this is an implementation of the DDPG algorithm to train an agent how to move a double jointed arm within moving target.

## environment details
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

## Dependencies & requirements to get started

1. To get up and running, you'll want to download the defined Udacity dependencies [here](https://github.com/udacity/deep-reinforcement-learning#dependencies)

2. You'll need to grab the following:
    - Unity ML agents: [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md)
    - NumPy: [here](http://www.numpy.org/) 
    - PyTorch: [here](https://pytorch.org/) 

3. Next you'll need the navigation simulation. Download the environment that corresponds to your operating system. 
- **_Version 1: One (1) Agent_**
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)
   
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip) (version 1) or [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) (version 2) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)

4. Move the downloaded file to the `p2_continuous-control/` folder in the DRLND repository. Decompress the file and you'll be ready to go. 
   
5. Navigate to the `Continuous_Control.ipynb` and load the file using the drlnd kernel. 

Credit to Udacity for collating the above resources
