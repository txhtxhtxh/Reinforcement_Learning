# Reinforcement Learning

## 1. Methods

### (1) Value based: Learn Q function

Generalized Policy Iteration: In GPI, the value function becomes close to the true value under current policy. At the same time, the policy becomes closer to the optimality.

![GPI](/Users/txh/Desktop/实习/Preparation/GPI.png)

对值函数取argmax生成Pi(s)，对于value based的方法，都是采用这样的策略来求得action

##### 特性

​		1) Value based 方法只适合离散的action情况，因为要取argmax_a Q(s,a)

​		2)  Value based 方法只适合 deterministic policy (确定性策略) 的情况

### (2) Policy based: Learn Policy

**Policy based**: maximize the expected return by optimizing policy

**On-policy**: 用于更新迭代的数据是由当下策略生成的

##### Classical way: Policy gradient

Loss : $$-log(\pi(a_t|s_t))\cdot Q(s_t,a_t)$$ or $$-log(\pi(a_t|s_t))\cdot (Q(s_t,a_t) - \hat{V}(s_t,a_t))$$(baseline) ，when the probability of an action is small but the reward is large the loss would be large

### (3) DP, MC, TD



## 2. Classic algorithms

​	(1) DQN: dual critic

​		off policy导致 target Q与 Q同步更新，无法收敛，故采取该方法让target Q网络是每隔一段时间才会更新

![dqn](/Users/txh/Github/figure/dqn.jpg)

​	(2) AC: PG(with baseline) + Value(Q-learning error)

​		AC + baseline = A2C

​		A2C + parallel = A3C

​	(3) DDPG: dual actor-critic

​		四套网络，actor,critic各两个，采取target和predict两个网络，避免像DQN一样的问题无法收敛

​	(4) TRPO / PPO

​	Based on policy gradient

​	$$\max_{\theta}\ \mathbb{E}_{s\sim\rho_{\theta_{old}},a\sim q}\left[\frac{\pi_{\theta}(a|s_n)}{q(a|s_n)}Q_{\theta_{old}}(s_n,a)\right],\\
{\rm subject}\ to\ \mathbb{E}_{s\sim\rho_{\theta_{old}}}\left[D_{KL}(\pi_{\theta_{old}}(\cdot|s)||\pi_{\theta}(\cdot|s))\right]\leq\delta$$

## 3. Algorithm

(1) Importance sampling