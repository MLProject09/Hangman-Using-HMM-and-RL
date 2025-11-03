# 🧩 Hangman Using HMM and Reinforcement Learning (RL)

A hybrid AI agent that plays the game of **Hangman** intelligently using a combination of **Hidden Markov Models (HMMs)** and **Reinforcement Learning (Q-Learning)**.  
The system learns word patterns using HMMs trained on a given text corpus and improves its letter-guessing policy through trial-and-error using RL.

---

## 🎯 Project Overview

This project integrates two core AI components:

1. **Hidden Markov Model (HMM):**
   - Learns letter transition probabilities from a training corpus.
   - Acts as a *language model* that predicts likely next letters based on observed positions and patterns.
   - Helps initialize the RL agent with better priors.

2. **Reinforcement Learning (RL) Agent:**
   - Uses **Q-Learning** to improve guessing strategy through repeated Hangman gameplay.
   - Learns which letters to guess under different word states (e.g., `_A__E`) to maximize reward (win rate, fewer wrong guesses).
   - Combines exploration (trying new guesses) and exploitation (using learned knowledge).

Together, the HMM provides probabilistic priors for letter prediction, while RL refines those predictions based on actual gameplay performance.

---

## ⚙️ Architecture

      +-----------------------+
      |   Training Corpus     |
      +----------+------------+
                 |
                 v
     +-----------+-----------+
     |  Hidden Markov Model  |
     | (learns letter patterns)
     +-----------+-----------+
                 |
      HMM probabilities guide RL
                 |
                 v
     +-----------+-----------+
     |  RL Agent (Q-Learning) |
     |  (learns optimal guesses)
     +-----------+-----------+
                 |
                 v
          +-------------+
          |  Hangman Env |
          +-------------+

---

## 🧠 Key Components

| Component | Description |
|------------|-------------|
| **HangmanEnv** | Simulates the Hangman game environment with rewards and penalties. |
| **HMM Trainer** | Learns emission and transition probabilities from a given corpus. |
| **Q-Learning Agent** | Learns the best guessing strategy based on state (current word pattern) and reward. |
| **Integration Layer** | Uses HMM probabilities as priors to guide RL exploration during learning. |

---

## 🧩 Workflow

1. **Train the HMM**  
   Load a text corpus (`corpus.txt`) and train an HMM that models letter transitions.

2. **Initialize the RL Agent**  
   The Q-table is initialized with letter-based states, influenced by HMM predictions.

3. **Train the RL Agent**  
   The agent plays multiple Hangman episodes using exploration and exploitation.

4. **Evaluate the Model**  
   The trained agent is tested on unseen words (`test.txt`) to measure success rate.

---
## 📂 Project Structure

```
Hangman-Using-HMM-and-RL/
│
├── corpus.txt           # Training words
├── test.txt             # Test words for evaluation
├── HMM_RL.ipynb
└── README.md
```

