
---

# Lecture 1 – Introduction to Reinforcement Learning

## What is Reinforcement Learning?

Reinforcement Learning is learning **through interaction with an environment** to maximize cumulative reward.

Key idea:

An **agent interacts with an environment over time** and learns from rewards.

At each time step:

- observe state $S_t$
- choose action $A_t$
- receive reward $R_{t+1}$
- transition to next state $S_{t+1}$

Goal:

Maximize **expected return**.

---

## RL vs Supervised Learning

Supervised learning:

- labeled dataset
- IID samples
- prediction problem

Reinforcement learning:

- **no labeled data**
- learning from **trial and error**
- **data depends on actions taken**

Key property:

RL data is **not IID**.

---

## Three Key Characteristics of RL

Your professor emphasized these.

1. **Closed-loop learning**

Actions influence future data.

2. **No direct instructions**

Agent must discover which actions are good.

3. **Delayed consequences**

Rewards may appear long after actions.

---

## Agent–Environment Interaction

The RL interaction loop:

$$
S_t \rightarrow A_t \rightarrow R_{t+1}, S_{t+1}
$$

Agent chooses action.

Environment responds with:

- reward
- next state

---

# Return (Total Future Reward)

Definition:

$$
G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \cdots
$$

Recursive form:

$$
G_t = R_{t+1} + \gamma G_{t+1}
$$

Variables:

- $G_t$ = return
- $R_{t+1}$ = immediate reward
- $\gamma$ = discount factor

Meaning:

Future rewards are **discounted**.

---

# Markov Property

A process is Markov if:

$$
P(S_{t+1} | S_t, S_{t-1}, ..., S_0)
=
P(S_{t+1} | S_t)
$$

Meaning:

The **current state contains all necessary information about the past**.

---

# Markov Decision Process (MDP)

An MDP is defined by:

$$
(S, A, P, R, \gamma)
$$

Where:

- $S$ = states
- $A$ = actions
- $P(s'|s,a)$ = transition probability
- $R$ = reward function
- $\gamma$ = discount factor

Transition probability:

$$
p(s',r|s,a)
$$

Probability of going to state $s'$ and receiving reward $r$.

---

# Policy

A policy defines agent behavior.

$$
\pi(a|s) = P(A_t = a | S_t = s)
$$

Meaning:

Probability of choosing action $a$ in state $s$.

---

# State Value Function

Expected return starting in state $s$:

$$
v_\pi(s) = \mathbb{E}_\pi[G_t \mid S_t = s]
$$

---

# Action Value Function

Expected return taking action $a$ in state $s$:

$$
q_\pi(s,a) = \mathbb{E}_\pi[G_t \mid S_t=s, A_t=a]
$$

---

# Bellman Equation Derivation

Start from return definition:

$$
G_t = R_{t+1} + \gamma G_{t+1}
$$

State value definition:

$$
v_\pi(s) = \mathbb{E}_\pi[G_t \mid S_t = s]
$$

Substitute:

$$
v_\pi(s) = \mathbb{E}_\pi[R_{t+1} + \gamma G_{t+1} \mid S_t = s]
$$

Expand expectation:

$$
v_\pi(s) =
\sum_a \pi(a|s)
\sum_{s',r}
p(s',r|s,a)
[r + \gamma v_\pi(s')]
$$

This is the **Bellman expectation equation**.

Meaning:

> Value of a state equals expected immediate reward plus discounted value of next state.

---

# Bellman Optimality Equations

Optimal state value:

$$
v_*(s)=
\max_a
\sum_{s',r}
p(s',r|s,a)
[r+\gamma v_*(s')]
$$

Optimal action value:

$$
q_*(s,a)=
\sum_{s',r}
p(s',r|s,a)
[r+\gamma \max_{a'} q_*(s',a')]
$$

Key idea:

Expectation over policy becomes **max over actions**.

---

# Dynamic Programming

Assumes **model is known**.

Meaning:

- transition probabilities known
- reward function known

Methods:

- Policy evaluation
- Policy iteration
- Value iteration

---

# Lecture 2 – Multi-Armed Bandits

Bandit problem:

Agent repeatedly chooses between actions with unknown rewards.

Goal:

Maximize cumulative reward.

---

# Exploration vs Exploitation

Exploration:

Try actions to learn about them.

Exploitation:

Choose action believed to be best.

Core challenge of bandits.

---

# Action Value Estimate

Expected reward of action $a$:

$$
Q_t(a) =
\frac{\sum_{i=1}^{t} R_i \mathbf{1}_{A_i=a}}
{\sum_{i=1}^{t} \mathbf{1}_{A_i=a}}
$$

Meaning:

Average reward observed for action $a$.

---

# Incremental Update Rule

Instead of storing all rewards:

$$
Q_{n+1} =
Q_n +
\frac{1}{n}
(R_n - Q_n)
$$

General update:

$$
Q_{n+1} =
Q_n +
\alpha (R_n - Q_n)
$$

Where $\alpha$ is the learning rate.

---

# ε-Greedy Strategy

Action selection rule:

- best action with probability $1-\epsilon$
- random action with probability $\epsilon$

Used to balance exploration and exploitation.

---

# Thompson Sampling

Bayesian exploration method.

Each arm has parameter:

$$
\theta_k \sim Beta(\alpha_k,\beta_k)
$$

Algorithm:

1. sample $\theta_k$ from each posterior
2. choose arm with largest sampled value
3. observe reward
4. update posterior

Posterior update:

Success:

$$
\alpha_k = \alpha_k + 1
$$

Failure:

$$
\beta_k = \beta_k + 1
$$

Key intuition:

> Thompson Sampling chooses actions with probability equal to the probability they are optimal.

---

# Monte Carlo Learning

Uses **complete episodes**.

Update rule:

$$
V(S_t) \leftarrow
V(S_t) + \alpha(G_t - V(S_t))
$$

---

# Temporal Difference Learning

Uses **bootstrapping**.

TD(0):

$$
V(S_t) \leftarrow
V(S_t) + \alpha
(R_{t+1} + \gamma V(S_{t+1}] - V(S_t))
$$

---

# SARSA

On-policy control:

$$
Q(S_t,A_t) \leftarrow
Q(S_t,A_t) +
\alpha
[R_{t+1} + \gamma Q(S_{t+1},A_{t+1}) - Q(S_t,A_t)]
$$

---

# Q-Learning

Off-policy control:

$$
Q(S_t,A_t) \leftarrow
Q(S_t,A_t) +
\alpha
[R_{t+1} + \gamma \max_a Q(S_{t+1},a) - Q(S_t,A_t)]
$$

---

# Deep Q Network (DQN)

Approximates Q values with neural network:

$$
Q(s,a;\theta)
$$

Training target:

$$
y = r + \gamma \max_{a'} Q(s',a';\theta^-)
$$

Important techniques:

- Experience Replay
- Target Network

---

# Most Important Oral Questions

1. What is the Markov property?
2. What defines an MDP?
3. What is a policy?
4. What is a value function vs Q function?
5. Derive the Bellman expectation equation.
6. Difference between Bellman expectation and optimality equations.
7. Monte Carlo vs TD learning.
8. SARSA vs Q-learning.
9. Why does DQN use replay buffers and target networks?
10. How does Thompson Sampling work?
