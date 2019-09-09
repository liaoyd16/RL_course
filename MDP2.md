###MDP2: Continuing-task-MDP

For the second MDP, I would present an MDP featuring a continuous task. Here, let us consider a central bank of a government manipulating interest rate.

##### State

For simplicity's sake, let us assume that the central bank adjusts benchmark interest rate based on CPI and total credit in the market. $S_t = (CPI_t, Cr_t, rate_t)$.

#####Action

What the central bank could do is to raise or lower interest rate. Action of time t is $A_t = rate_t - rate_{t-1}$. Notice that we shall constrain $A_t$ to be larger than or equal to zero when $rate_{t-1} = 0$ in common cases, since we don't want minus interest rate.

##### Reward

The purpose of interest rate manipulation is to stablize the market, preventing severe inflation and deflation. For a time period when general price level is above tolerable level, we penalize the central bank with an amount proportional to the exceed; for a time period when price level is below tolerable level, we penalize as aforesaid; for a time when price level is not exceeding certain limits, we award with a constant value.