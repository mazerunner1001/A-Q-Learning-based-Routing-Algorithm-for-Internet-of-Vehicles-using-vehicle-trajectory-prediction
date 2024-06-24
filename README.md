<div align="center">

# Q-Learning Based Routing in Vehicular Networks
</div>

This repository contains the implementation and simulation code for the unpublished research paper on Q-Learning based routing in vehicular networks. The code simulates the routing of data packets using a combination of Q-Learning and ARIMA time series models to predict vehicle locations and make routing decisions.

## Description
The nodes that receive the INFO packets sent by the current node are considered its neighbors. An optimal route from the source to the desired destination nodes is determined by sending a data packet from the source node and selecting the intermediate (neighboring) nodes for forwarding using the proposed Q-learning model until it reaches the destination node.

## Key Steps:
1. Calculate stability, continuity, and resource factors of all neighboring nodes to determine the reward value of the Q-learning model for forwarding the data packet.
2. Use the Bellman equation to train the Q-learning model to get the corresponding Q values, which are used to fill the Q table.
3. Use the ARIMA time series model to predict the future location of a particular vehicle at the time instant when the data packet is assumed to arrive at the next hop node.
4. Calculate the Distance factor to direct the data packet toward the destination node.
5. Integrate the initial Q values with the distance factor to find the Enhanced Q values, which are then used to select the next hop node greedily.

## Classes and Functions
- Vehicle Class
  - This class encapsulates the properties of a vehicle within the network.

- MapEnv Class
  - A subclass of gym.Env, this class models the environment in which vehicles operate. It defines the state and action spaces, and includes methods for calculating distance, spatial factor, connectivity factor, and resource factor used in reward calculation.

- Packet Class
  - This class represents a packet that needs to be transmitted from a source vehicle to a destination vehicle.

- init_dataset Function
  - Initializes a dataset of vehicles with random positions and calculates the number of neighbors for each vehicle based on a given neighbor distance.

- Q_learning Function
  - Implements the Q-learning algorithm to learn the optimal policy for routing packets.

- get_df_table Function
  - Calculates the directional factor (DF) table for each vehicle based on its current position, destination, and neighbors.

- Result Class
  - Represents the result of a simulation, including whether the packet was successfully delivered, times for Q-learning, ARIMA forecasting, packet transmission, number of information packets, and the time index at which the simulation ended.

### Main Simulation Loop
The main loop of the script runs simulations for different time intervals and calculates metrics such as packet delivery ratio, average end-to-end delay, and routing overhead ratio by iteratively simulating vehicle movements, updating rewards and DF tables, and running Q-learning and ARIMA forecasting to make routing decisions.

## Installation
Clone the repository:
  ```bash
  git clone https://github.com/mazerunner1001/A-Q-Learning-based-Routing-Algorithm-for-IoV.git
  cd A-Q-Learning-based-Routing-Algorithm-for-IoV
  ```
Create and activate a virtual environment:
  ```bash
  python -m venv venv
  source venv/bin/activate  # On Windows: venv\Scripts\activate
  ```
Install the required packages:
  ```bash
  Copy code
  pip install -r requirements.txt
  
```

## Usage
Run the main simulation script:
  ```bash
  python main.py
  ```

### Dependencies
- numpy
- gym
- tqdm
- datetime
- matplotlib
- statsmodels

## Results
The results of the simulation include metrics such as packet delivery ratio, average end-to-end delay, and routing overhead ratio. These are calculated and plotted for different time intervals.
