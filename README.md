# RL-SAC: Reinforcement Learning for VIMA

This repository contains the implementation of **Soft Actor-Critic (SAC)** and **Proximal Policy Optimization (PPO)** algorithms to train a visually impaired agent to navigate a custom environment called **VIMA (Visual Impairment Motion Assistant)**.

This code accompanies the tutorial article:  
[**Medium Article: Training a Visually Impaired Agent with RL**](https://medium.com/@dineth330/draft-ppo-2ac39ca9ee7c)

## 📌 Project Overview

The goal of this project is to train an autonomous agent to navigate a 2D space, avoiding static obstacles and moving "humans" to reach a specific target. The agent utilizes simulated **Lidar** readings for perception and continuous control for movement.

Two major Reinforcement Learning algorithms are compared:
1.  **Soft Actor-Critic (SAC)**: An off-policy, maximum entropy deep RL algorithm known for sample efficiency and exploration.
2.  **Proximal Policy Optimization (PPO)**: An on-policy gradient method (specifically **Recurrent PPO** with LSTM is used here) known for stability and ease of tuning.

## 📂 Repository Structure

- **`SAC.ipynb`**: Complete implementation of the Soft Actor-Critic algorithm. Includes the custom `VIMAEnv` environment, training loop with custom callbacks, and visualization of loss/reward metrics.
- **`PPO.ipynb`**: Implementation using Recurrent PPO (LSTM policy) to handle state memory, optimizing for the same VIMA environment.

## 🛠️ Dependencies

To run the notebooks, you will need the following Python libraries. You can install them via pip:

```bash
pip install gymnasium stable-baselines3 sb3-contrib imageio matplotlib opencv-python pandas seaborn shimmy

```

*Note: `sb3-contrib` is required for the RecurrentPPO implementation used in `PPO.ipynb`.*

## 🧠 The Environment: VIMA

The custom **VIMAEnv** is a Gymnasium-compatible environment defined within the notebooks.

* **Observation Space**:
* 360-degree Lidar scan (distances to obstacles/humans).
* Target distance and angle.
* Agent's current velocity.


* **Action Space**: Continuous control `[Speed, Rotation]`.
* **Rewards**:
* Positive reward for moving closer to the target.
* Large bonus (`+100`) for reaching the target.
* Penalty (`-50`) for collisions.
* Small step penalty (`-0.1`) to encourage speed.



## 🚀 Usage

1. Clone the repository:
```bash
git clone [https://github.com/Dineth5/RL-SAC.git](https://github.com/Dineth5/RL-SAC.git)
cd RL-SAC

```


2. Open the desired notebook (`SAC.ipynb` or `PPO.ipynb`) in Jupyter or Google Colab.
3. Run all cells to initialize the environment and start training.

The notebooks include custom callbacks (`EpisodeLoggerCallback` / `PPOLoggingCallback`) that log internal metrics (Actor Loss, Critic Loss, Entropy) which are visualized at the end of the training session.

## 📊 Results

The notebooks generate training graphs showing:

* **Episode Rewards**: Improvement in agent performance over time.
* **Losses**: Actor and Critic loss convergence.
* **Entropy**: How the agent balances exploration vs. exploitation (critical for SAC).

## 🔗 References

* **Tutorial**: [Medium Article](https://medium.com/@dineth330/draft-ppo-2ac39ca9ee7c)
* **Libraries**: [Stable-Baselines3](https://github.com/DLR-RM/stable-baselines3)

```

```
