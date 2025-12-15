# Minesweeper_AI

## 🎯 Project Overview
This project is using numerous AIs (bots) to compete against each other in the game Minesweeper. These range from very basic AI systems to much more advanced systems that use neural networks to reason sequentially. The intended goal of this project is to understand how the various machine learning techniques can address the logic problems inherent in Minesweeper.

### Key Features
- 3 Distinct AI Approaches: Rule-based logic, neural prediction, and actor-critic reinforcement learning
- Sequential Reasoning: Neural network that "thinks longer" to improve decisions
- Comprehensive Evaluation: Statistical comparison across difficulty levels
- Visualization Tools: Heatmaps showing how AI predictions evolve with thinking time

## 📋 Project Structure
1. MinesweeperGame - Game environment simulator
- Board generation with safe first-click guarantee
- Game state management and win condition tracking
- State representation for neural network input

2. LogicBot - Rule-based deterministic bot
- Logical inference using Minesweeper rules
- Probability estimation for uncertain situations
- Conservative guessing strategy

3. Neural Network Models:
- MinePredictor - CNN with residual blocks and attention
- SequentialThinker - Multi-step reasoning with GRU cells
- Actor-Critic - Separate networks for move selection (actor) and state evaluation (critic)

4. Training & Evaluation Pipeline:
- Synthetic data generation for supervised learning
- Comprehensive evaluation with confidence intervals
- Performance comparison against baseline logic bot

## 📊 Performance Metrics

### Logic Bot vs Neural Bot
Training Neural Bot to beat Logic Bot:
- Final training loss: 0.3273
- Final validation loss: 0.4040
- Consistent learning observed over 15 epochs

<img width="582" height="184" alt="Screenshot 2025-12-14 at 7 38 09 PM" src="https://github.com/user-attachments/assets/e371cdc4-b201-4a1c-941a-984af48c8a9d" />

#### Key Findings
- Neural bot achieves higher win rate (64% vs 48%)
- Neural bot makes decisions significantly faster (88 vs 205 steps)
- The neural network learns to play more aggressively but successfully

### Logic Bot vs Actor-Critic Bot
Data Generation:
- Generated 917 training samples with diverse survival outcomes
- Survival statistics: Mean = 0.752, Std = 0.294 (good variance)
- Distribution: 40.5% high-survival (>0.8), 15.1% low-survival (<0.4)

Critic Training (15 epochs):
- Final R² score: 0.5010 (moderate predictive power)
- Training loss improved: 0.1113 → 0.0421
- Validation loss: 0.0841 → 0.0417

Actor Training (6 epochs):
- Limited data: Only 18 actor samples generated
- Training loss decreased: 4.6819 → 4.0724
- Average best move probability: 0.556

#### Evaluation Results:
- Critic shows meaningful learning (R² = 0.501)
- Actor training completed but with limited data
- Neural bots didn't beat Logic Bot in final evaluation

#### Challenges Identified:
- Insufficient actor training data (only 18 samples)
- High mine density makes logic bot comparisons difficult
- Actor-critic bootstrapping requires more iterations

### Sequential Thinking
<img width="524" height="363" alt="Screenshot 2025-12-14 at 7 42 15 PM" src="https://github.com/user-attachments/assets/55bf32cd-6641-408a-95d0-7dedd5636a1d" />

#### Key Insights:
- More thinking improves performance: 10-step thinker achieves 70% win rate vs Logic Bot's 40%
- Non-monotonic improvement: Performance dips at intermediate steps (3,5) then improves
- Speed vs accuracy: Neural bots make decisions 2x faster than logic bot

## 📈 Performance Summary
<img width="686" height="219" alt="Screenshot 2025-12-14 at 7 44 00 PM" src="https://github.com/user-attachments/assets/8c5db2a8-2c2d-436f-a46d-06d1e98ddfe4" />

### 🎯 Overall Project Achievements

#### ✅ Successfully Demonstrated:
- Neural networks can learn Minesweeper - Achieved 64-70% win rates
- Sequential reasoning helps - More thinking steps → better decisions
- Actor-critic learning principles - Critic learned to predict survival (R^2 = 0.501)
- Comprehensive evaluation framework - Statistical comparisons with confidence intervals

#### 🔍 Key Technical Insights:
- Data quality matters: Critic needed diverse survival outcomes to learn
- Conservative vs aggressive: Neural bots play faster but riskier
- Thinking time trade-off: More computation improves accuracy but increases inference time
- Baseline strength: Logic bot remains competitive due to Minesweeper's deterministic nature
