
Given your timeline, do not try to master everything evenly.

You are already solid on lecture 1 and decent on lecture 2, so the highest-return move is:

1. **Lock in MDPs and Bellman equations first**
    
2. **Then Dynamic Programming**
    
3. **Then MC vs TD, SARSA vs Q-learning**
    
4. **Then DQN basics**
    
5. **Then Thompson Sampling**, because he may pick one question from there
    

The exam emphasis you mentioned fits the slide progression very closely: MDP formalism, Bellman expectation/optimality, DP, then model-free learning, then DQN. The uploaded decks explicitly cover Bellman expectation equations in the MDP lecture, policy evaluation / policy iteration / value iteration in DP, model-free prediction and control in the MC/TD decks, and DQN extensions in the DQN deck.

## What to memorize for the oral section

You need to be able to do two things well:

- **Define every symbol in the equation**
    
- **Explain why the equation makes sense in words**
    

That is usually what saves people in oral exams.

---

# 1. Bellman equation, derived in the cleanest way

Start from the definition of return:

[  
G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \cdots  
]

So recursively,

[  
G_t = R_{t+1} + \gamma G_{t+1}  
]

Now define the state-value function under policy (\pi):

[  
v_\pi(s) = \mathbb{E}_\pi[G_t \mid S_t = s]  
]

Substitute the recursive form of return:

[  
v_\pi(s) = \mathbb{E}_\pi[R_{t+1} + \gamma G_{t+1} \mid S_t = s]  
]

Use linearity of expectation:

[  
v_\pi(s) = \mathbb{E}_\pi[R_{t+1} \mid S_t = s] + \gamma \mathbb{E}_\pi[G_{t+1} \mid S_t = s]  
]

Now the next return depends on the next state, so:

[  
\mathbb{E}_\pi[G_{t+1} \mid S_t = s] = \sum_{s'} P(s' \mid s,\pi), v_\pi(s')  
]

More explicitly, since policy chooses actions:

[  
v_\pi(s)=\sum_a \pi(a\mid s)\sum_{s',r} p(s',r\mid s,a)\bigl[r+\gamma v_\pi(s')\bigr]  
]

That is the **Bellman expectation equation** for (v_\pi). Your MDP lecture has Bellman expectation equations for (v_\pi), an example, and a matrix form.

### What “mean” means here

It is called the mean or expectation form because you are taking the **expected value** over all randomness:

- randomness in the action chosen by the policy
    
- randomness in the environment transition
    
- randomness in the reward
    

So in words:

> The value of a state equals the expected immediate reward plus discounted expected value of the next state.

That sentence is worth memorizing exactly.

---

# 2. Bellman equation for action-value

Definition:

[  
q_\pi(s,a)=\mathbb{E}_\pi[G_t \mid S_t=s, A_t=a]  
]

Then:

[  
q_\pi(s,a)=\sum_{s',r} p(s',r\mid s,a)\Bigl[r+\gamma \sum_{a'}\pi(a'\mid s')q_\pi(s',a')\Bigr]  
]

In words:

> If I force action (a) now in state (s), the Q-value is the expected immediate reward plus discounted value of what happens afterward when I go back to following policy (\pi).

---

# 3. Bellman optimality equations

For optimal state-value:

[  
v__(s)=\max_a \sum_{s',r} p(s',r\mid s,a)\bigl[r+\gamma v__(s')\bigr]  
]

For optimal action-value:

[  
q__(s,a)=\sum_{s',r} p(s',r\mid s,a)\Bigl[r+\gamma \max_{a'} q__(s',a')\Bigr]  
]

Key oral point:

- **Expectation equation** uses the policy average
    
- **Optimality equation** replaces that average with a **max**, because the agent acts optimally
    

Your MDP deck includes Bellman expectation and Bellman optimality examples.

---

# 4. What to say if he asks “What is an MDP?”

Use this structure:

An MDP models sequential decision making with:

- **states** (S_t)
    
- **actions** (A_t)
    
- **transition probabilities** (p(s' \mid s,a))
    
- **rewards**
    
- **policy** (\pi(a\mid s))
    

The Markov property means:

> The future depends only on the current state and action, not the full past history.

The MDP lecture explicitly builds from Markov process to Markov reward process to Markov decision process.

---

# 5. Dynamic Programming, in simple words

Dynamic programming assumes the model is known:

- reward function known
    
- transition probabilities known
    

Then you can compute values by repeated backups.

The DP lecture is centered on policy evaluation, policy iteration, and value iteration.

### Policy evaluation

Given a fixed policy (\pi), compute (v_\pi).

### Policy improvement

Make the policy greedy with respect to the current value estimates.

### Policy iteration

Alternate:

1. evaluate policy
    
2. improve policy
    

### Value iteration

Instead of fully evaluating a policy, repeatedly apply the Bellman optimality backup.

Good oral sentence:

> Policy iteration alternates between asking “How good is this policy?” and “Can I improve it?” Value iteration collapses those into direct optimality backups.

---

# 6. MC vs TD

The model-free prediction deck contrasts these directly.

## Monte Carlo

- learns from **complete episodes**
    
- uses actual sampled return
    
- no bootstrapping
    

Update idea:

[  
V(S_t) \leftarrow V(S_t) + \alpha\bigl(G_t - V(S_t)\bigr)  
]

## Temporal Difference

- updates **before episode ends**
    
- bootstraps from current estimate
    

Basic TD(0):

[  
V(S_t) \leftarrow V(S_t) + \alpha\bigl(R_{t+1}+\gamma V(S_{t+1})-V(S_t)\bigr)  
]

Best oral explanation:

> Monte Carlo waits for the real final outcome. TD updates immediately using one-step lookahead and its own current estimate.

### Bootstrap meaning

Bootstrapping means you update an estimate using another estimate instead of waiting for the full truth.

That idea matters a lot.

---

# 7. Control: SARSA vs Q-learning

The model-free control lecture is very likely testable. It includes on-policy and off-policy learning, (\epsilon)-greedy, and model-free policy iteration using action-value functions.

## SARSA

On-policy.

[  
Q(S_t,A_t)\leftarrow Q(S_t,A_t)+\alpha\bigl[R_{t+1}+\gamma Q(S_{t+1},A_{t+1})-Q(S_t,A_t)\bigr]  
]

It uses the **actual next action taken**.

## Q-learning

Off-policy.

[  
Q(S_t,A_t)\leftarrow Q(S_t,A_t)+\alpha\bigl[R_{t+1}+\gamma \max_a Q(S_{t+1},a)-Q(S_t,A_t)\bigr]  
]

It uses the **best possible next action**, not necessarily the one actually taken.

### Easy oral distinction

- **SARSA** learns the value of the policy it is actually following
    
- **Q-learning** learns toward the greedy optimal policy even while behaving exploratorily
    

If he asks why Q-learning is off-policy:

> because behavior can be (\epsilon)-greedy, but the target uses the greedy max action

---

# 8. DQN basics

Your DQN deck is about DQN and extensions, and includes replay and dueling DQN.

Core idea:

> DQN uses a neural network to approximate (Q(s,a)) when the state space is too large for a table.

Instead of storing a table of Q-values, use:

[  
Q(s,a;\theta)  
]

### Why plain Q-learning is hard with neural nets

Because:

- consecutive samples are correlated
    
- targets keep changing while the network learns
    

### Two classic DQN fixes

1. **Experience replay**  
    store transitions and sample random mini-batches  
    this breaks correlation and reuses data
    
2. **Target network**  
    use a delayed copy of the Q-network to compute targets  
    this stabilizes learning
    

### DQN target

[  
y = r + \gamma \max_{a'} Q(s',a';\theta^-)  
]

where (\theta^-) are target network parameters.

### Dueling DQN

The deck notes that sometimes action differences are not very important in some states, so separating state value from action advantage can help robustness.

Talk track:

> Dueling DQN decomposes Q into a state-value part and an action-advantage part, so the network can learn whether a state is good even when the action choice matters little.

You probably do **not** need every extension in detail unless it came up in quiz questions.

---

# 9. Thompson Sampling, high-yield version

This comes from your uploaded Thompson tutorial and bandit notes.

## Core idea

Thompson Sampling is a Bayesian exploration method for bandits.

At each round:

1. maintain a posterior belief about each arm’s reward parameter
    
2. sample a plausible parameter from each posterior
    
3. choose the arm with the highest sampled value
    
4. observe reward
    
5. update the posterior
    

## Beta-Bernoulli case

If rewards are binary, each arm has unknown success probability (\theta_k).  
Start with prior:

[  
\theta_k \sim \text{Beta}(\alpha_k,\beta_k)  
]

After choosing arm (k):

- success: ((\alpha_k,\beta_k)\leftarrow(\alpha_k+1,\beta_k))
    
- failure: ((\alpha_k,\beta_k)\leftarrow(\alpha_k,\beta_k+1))
    

The tutorial states the posterior stays Beta and updates by adding success/failure pseudo-counts.

### Why TS works intuitively

It explores arms that still have meaningful uncertainty, but not uniformly at random.

Good oral sentence:

> Thompson Sampling does probability matching. It chooses an arm with probability roughly equal to the probability that the arm is actually optimal under the current posterior.

## Regret idea

Bandit regret is the gap between the reward of always pulling the best arm and the reward actually collected. The Thompson tutorial defines cumulative regret as the sum over time of best mean reward minus chosen arm mean reward.

That is enough for a midterm answer unless he asks for more theory.

---

# 10. The 10 most likely short-answer questions

These are what I would drill tonight:

1. **What is the Markov property?**
    
2. **Define policy, value function, and action-value function.**
    
3. **Derive the Bellman expectation equation for (v_\pi(s)).**
    
4. **Difference between Bellman expectation and Bellman optimality equations.**
    
5. **What is policy evaluation vs policy iteration vs value iteration?**
    
6. **Difference between Monte Carlo and TD learning.**
    
7. **What does bootstrapping mean in RL?**
    
8. **Difference between SARSA and Q-learning.**
    
9. **Why do DQN methods use replay buffer and target network?**
    
10. **How does Thompson Sampling choose actions and update beliefs?**
    

If you can answer those clearly out loud, you are in much better shape.

---

# 11. Best use of your remaining time

## Tonight

Spend most time on:

- MDP
    
- Bellman equations
    
- DP
    
- MC vs TD
    
- SARSA vs Q-learning
    
- DQN basics
    
- Thompson Sampling basics
    

## Tomorrow before exam

Do only active recall:

- say equations out loud
    
- define every symbol
    
- explain each equation in plain English
    
- compare similar concepts
    

Do not reread every slide passively.

---

# 12. Best oral-answer template

For almost any equation, answer in this format:

1. **State what it represents**
    
2. **Define symbols**
    
3. **Explain the intuition**
    
4. **Say how it differs from nearby equations**
    

Example for Bellman expectation:

> This equation gives the value of a state under policy (\pi).  
> (v_\pi(s)) is expected return from state (s), (\pi(a\mid s)) is the probability of taking action (a), and (p(s',r\mid s,a)) is the probability of transitioning to next state (s') with reward (r).  
> The equation says value equals expected immediate reward plus discounted expected future value.  
> It differs from the Bellman optimality equation because expectation over policy is replaced by a max over actions.

That style will sound strong in an oral exam.

---

# 13. Most important warning

Do not get stuck trying to memorize every detail of function approximation or all DQN extensions. Your safest points are in:

- MDP formalism
    
- Bellman equations
    
- DP
    
- TD / Q-learning / SARSA
    
- one clean Thompson Sampling explanation
    

Those are much more likely to matter.

Send me one concept at a time now, and I will turn it into a **midterm-ready short-answer plus oral-answer script**.