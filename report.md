# **Project3. Collaboration and Competition** 

## Report

---

[//]: # (Image References)
[image1]: ./result.png "Visualization"
[image2]: ./result_average.png "Visualization"


**Learning Algorithm**
* DDPG\
 This algorithm has four networks, actor target, actor local, critic target and critic local. Each target network is used for training, and is soft-updated by each local network.\
 
 This implementation is shown in model.py and ddpg_agent.py.

  My final actor network model consisted of the following layers:
  | Layer         		    |   Description	           		                      |
  |:----------------------|:--------------------------------------------------| 
  | (1)Input         		  |   24 dimensions states                            | 
  | (2)Batch Normalization|                                                   |
  | (3)Fully connected		|   input 24, outputs 400                           |
  | (4)ReLU		            |        									                          |
  | (5)Fully connected		|   input 400, outputs 300                          |
  | (6)ReLU		            |        									                          |
  | (7)Fully connected    |   input 300, outputs 2                            |
  | (8)tanh		            |                                                   |

  My final critic network model consisted of the following layers:
  | Layer         		    |   Description	           		                      |
  |:----------------------|:--------------------------------------------------| 
  | (1)Input         		  |   24 dimensions states                            | 
  | (2)Batch Normalization|                                                   |
  | (3)Fully connected		|   input 24, outputs 400                           |
  | (4)ReLU		            |        									                          |
  | (5)Concatinating		  |   input 400 + 2(action), outputs 402  				    |
  | (5)Fully connected		|   input 402, outputs 300                          |
  | (6)ReLU		            |        									                          |
  | (7)Fully connected    |   input 300, outputs 1                            |


* hyperparameter\
 Used hyperparameters are shown below. 

  - BUFFER_SIZE = int(2e6)  # replay buffer size
  - BATCH_SIZE = 128        # minibatch size
  - GAMMA = 0.99            # discount factor
  - TAU = 1e-3              # for soft update of target parameters
  - LR_ACTOR = 6e-4         # learning rate of the actor 
  - LR_CRITIC = 1e-3        # learning rate of the critic
  - WEIGHT_DECAY = 0        # L2 weight decay
  - LEARN_FREQ = 20         # how often to update the network
  - LEARN_NUM = 10          # the number of learning
  - theta = 0.15            # Ornstein-Uhlenbeck process parameter
  - sigma = 0.1             # Ornstein-Uhlenbeck process parameter
  - mu = 0.0                # Ornstein-Uhlenbeck process parameter



**Plot of Rewards**\
 The scores of DDPG show below.
 After 1395 Episodes, average score exceeds +0.5. \
 
 raw score

![alt text][image1]

 moving average(window size 100) score

![alt text][image2]



The scores when the model learning is below.
Average window size is 100 episodes.\

* DDPG\
Episode 100	Average Score: -0.00\
Episode 200	Average Score: -0.00\
Episode 300	Average Score: -0.00\
Episode 400	Average Score: 0.010\
Episode 500	Average Score: 0.01\
Episode 600	Average Score: 0.01\
Episode 700	Average Score: 0.000\
Episode 800	Average Score: 0.08\
Episode 900	Average Score: 0.05\
Episode 1000	Average Score: 0.05\
Episode 1100	Average Score: 0.05\
Episode 1200	Average Score: 0.05\
Episode 1300	Average Score: 0.14\
Episode 1400	Average Score: 0.30\
Episode 1495	Average Score: 0.50\
Environment solved in 1395 episodes!	Average Score: 0.50

**Ideas for Future Work**\
  In Addition to current learning algorithm, prioritized replay buffer should be implemented.\
  Probably, D4PG will get better result than current one.
