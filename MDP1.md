### MDP1: Episodic-task-MDP

First, I design an episodic-task-MDP with discrete states and actions. Let us consider a chess game.

#####State

Let the state $S_t$ be an array of size $64 = 8\times8$. Each pane's state is in a finite set $\{0, pawn_e, night_e, bishop_e, rook_e, queen_e, king_e, pawn_o, night_o, bishop_o, rook_o, queen_o, king_o\}$, where 0 represents 'no draughtsman in position', subscription $\dot{}_e$ and $\dot{}_o$ denotes whom the draughtsman belongs to (enemy or us). We can also think of the state as a function $S_t(p)$, $p$ is in set $\{(1,1),...,(8,8)\}$. If the game is finished, then the state is transformed into an all-blank-chessboard.

##### Action

Let the action $A_t$ be a tuple of positions: $(p_{start}, p_{end})$. This is easy to understand: for every action, a draughtsman moves from its position $p_{start}$ to a new position $p_{end}$. If the player decides to give up, it can make legal action: $((0,0),(0,0))$ to surrender.

##### Reward

First let us introduce certain tool functions:

>  $V(d)$ is a value function mapping a draughtsman $d$. 
>
> $I(p, S, A)$ is a boolean function judging wheter the movement is legal.

Let reward $R_t$ be a function of state $S_{t-1}$ and an action $A_{t-1}$: $R_{t}(S_{t-1}, A_{t-1}) = V(S_{t-1}(p_{end, t-1})) - 2\times INF\times I(p_{start, t-1},S_{t-1}(p_{start, t-1}),A_{t-1})$. The $2$ in front of the second term is imposed so that even a single illegal action can entail negative results.