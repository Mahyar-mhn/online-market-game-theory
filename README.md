# 🧠 Nash Equilibrium Online Market Simulation

A simulation of **competitive online sellers** using **Game Theory** concepts, where sellers adjust **price** and **advertising strategies** to reach a **Nash Equilibrium**.  
The model also integrates **social network influence** using a **NetworkX**-based customer graph.

---

## 📘 Project Overview

This project models a simplified **online marketplace** (like Amazon or Digikala) where multiple sellers offer similar products.  
Each seller decides:
- The **price** of the product (`pᵢ`)
- The **advertising budget** (`mᵢ`)

Customers choose which seller to buy from based on:
1. Product **price**
2. Seller **advertising level**
3. **Social influence** (recommendations, influencer effects)

The simulation finds the **Nash Equilibrium** where no seller can improve profit by unilaterally changing their strategy.

---

## ⚙️ Core Features

### 🧩 Data Preprocessing
- Cleans the dataset (`online_retail_II.xlsx`)
- Removes missing, duplicate, and invalid (negative) rows
- Aggregates product-level statistics

### 💸 Seller Simulation
- Creates **hypothetical sellers** with different prices and advertising budgets
- Defines fixed production costs
- Computes **demand** and **profit** functions per seller

### 🔁 Nash Equilibrium Modeling
- Iteratively updates sellers’ strategies (price & ads)
- Uses a **best-response algorithm** until equilibrium
- Detects convergence when sellers stop adjusting strategies

### 🌐 Social Network Integration
- Builds a **customer network** using `NetworkX` (Barabási–Albert graph)
- Assigns **influence coefficients** based on centrality (top 10% = influencers)
- Updates each seller’s influence based on their connected customers

### 📊 Visualization
- **Profit vs Price and Advertising**
- **2D Nash Equilibrium plots**
- **Social influence sensitivity (γ variation)**
- **Influence vs Demand**

---

## 📈 Mathematical Model

### Demand Function
\[
D_i = \text{base\_demand} + \alpha m_i + \beta (p_i - p_j) + \gamma \text{influence\_score}
\]

### Profit Function
\[
\Pi_i = (p_i - cost) D_i - m_i
\]

Equilibrium is reached when no seller can improve \(\Pi_i\) by changing \(p_i\) or \(m_i\).

---

## 🧮 Parameters

| Symbol | Description | Example Value |
|:-------|:-------------|:---------------|
| `base_demand` | Baseline demand for the product | 100 |
| `α` | Effect of advertising on demand | 0.05 |
| `β` | Sensitivity to price difference | -30 |
| `γ` | Effect of social influence | 20 |

---

## 🧰 Dependencies

```bash
pip install pandas numpy matplotlib seaborn networkx
