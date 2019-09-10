###MDP3: Continuous-state-MDP

For the third MDP, I would like to propose a MDP whose states and actions are continuous. Let us consider a thermometer that controls the temperature of a closed room. It attempts to control the temperature at a given value which is above ambient temperature. It has a sensor, a heater and a fan.

##### State

It is obvious that the state of the room is the temperature. That is, $S_t \in R_+$. We do not allow temperature below $0K$. Here, the time $t$ would be continuous rather than discrete in previous cases. We assume desired temperature is $T_0$.

##### Action

For the thermometer, it could manipulate a) fan power $a^{(1)}_t$ b) heater power $a^{(2)}_t$. We assume that these two are both above zero. Assume we want the thermometer to keep power consumption below a threshold $P_0$.

#####Reward

We consider the reward from two perspectives. 

First, we would punish the thermometer if it produces temperature perturbations. That is, during a small time interval $dt$, $(S_t - T_0)^2 dt$ is the amount of 'uncomfortness' during the time period. 

Second, we discourage the thermometer from spending too much power. We use $(a^{(1)}_t+a^{(2)}_t - P_0)dt$.

Hence, reward of a small time interval $dt$ is $[(S_t - T_0)^2 + a^{(1)}_t+a^{(2)}_t - P_0] dt$.