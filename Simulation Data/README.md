# 📊 Simulation Data

This directory contains the raw output data exported from the NetLogo simulations. Each Excel file corresponds to a specific experimental condition described in the project.

## 📂 File Descriptions

### 1. Modified Model I (Spread & Jump)
Data from the experiments testing the "Neighbor Spread" and "Information Jump" effects (Stage 1).

* **[📊 Modified Rebellion 1_..._SPREAD-table.xlsx](./Modified%20Rebellion%201_Probability%20of%20spread%20and%20Probability%20of%20jump_SPREAD-table.xlsx)**
    * **Scenario:** Simulation with only **Neighbor Spread** enabled.
    * **Focus:** How local interactions influence the spread of rebellion.

* **[📊 Modified Rebellion 1_..._JUMP-table.xlsx](./Modified%20Rebellion%201_Probability%20of%20spread%20and%20Probability%20of%20jump_JUMP-table.xlsx)**
    * **Scenario:** Simulation with only **Random Information Jump** enabled.
    * **Focus:** How non-local information diffusion affects the rebellion.

* **[📊 Modified Rebellion 1_..._SPREAD AND JUMP-table.xlsx](./Modified%20Rebellion%201_Probability%20of%20spread%20and%20Probability%20of%20jump%20_SPREAD%20AND%20JUMP-table.xlsx)**
    * **Scenario:** Simulation with **Both** Neighbor Spread and Random Jump enabled.
    * **Focus:** The combined effect of local and global diffusion.

### 2. Modified Model II (Regime Overthrow)
Data from the final model simulating the collapse of the regime (Stage 2).

* **[📊 Modified Rebellion 2_..._table.xlsx](./Modified%20Rebellion%202_Legitimacy%20feedback%20and%20Cops%20go%20quiet%20Modified%20Rebellion%202-table.xlsx)**
    * **Scenario:** Full model with **Dynamic Legitimacy** and **Rational Police Agents**.
    * **Outcome:** Shows the "Tipping Point" where police stop arresting (`quiet? = true`) and the regime is overthrown.

---

## 📝 Data Dictionary (Korean to English)

The raw data files contain headers in Korean. Use the tables below to understand each column.

### 1. General Info & Agent States (Common)
Basic simulation metrics available in all data files.

| Korean Header | English Translation | Description |
| :--- | :--- | :--- |
| **시뮬 회차** | **Simulation Run ID** | Identifier for the specific simulation run number. |
| **Tick** | **Ticks (Time)** | The time step of the simulation. |
| **폭동 시민** | **Active Agents** | Number of citizens actively rebelling (Red). |
| **조용한 시민** | **Quiet Agents** | Number of citizens currently inactive/quiet (Green). |
| **수감 시민** | **Jailed Agents** | Number of citizens currently in jail (Black). |
| **평균 수감 기간** | **Avg Jail Term** | The average remaining jail term of currently jailed agents. |

### 2. Agent Parameters (Mathematical Logic)
Variables related to the agents' decision-making process (*Grievance > Net Risk*).

| Korean Header | English Translation | Description |
| :--- | :--- | :--- |
| **시민의 위험 회피 평균** | **Avg Risk Aversion (R)** | Average risk aversion level of citizens (0.0~1.0). |
| **시민의 고난 평균** | **Avg Hardship (H)** | Average perceived hardship of citizens. |
| **시민의 불만 평균** | **Avg Grievance (G)** | Average grievance level calculated as `H * (1 - L)`. |
| **시민의 체포 확률 평균** | **Avg Arrest Prob (P)** | Average estimated probability of being arrested. |
| **시민의 순 위험 평균** | **Avg Net Risk (N)** | Average net risk calculated as `R * P`. |
| **시민의 행동 결정 공식 평균** | **Avg Decision Value (G-N)** | The average result of `Grievance - Net Risk`. If this > threshold, they rebel. |

### 3. Model 1 Specifics (Diffusion)
Columns found only in the *Spread & Jump* model files.

| Korean Header | English Translation | Description |
| :--- | :--- | :--- |
| **확산 횟수** | **Spread Count** | Number of agents activated via Neighbor Effect. |
| **점프 횟수** | **Jump Count** | Number of agents activated via Random Information Jump. |

### 4. Model 2 Specifics (Police & Regime)
Columns found only in the *Regime Overthrow* model files.

| Korean Header | English Translation | Description |
| :--- | :--- | :--- |
| **정부의 정당성** | **Gov Legitimacy (L)** | Dynamic legitimacy level of the regime. Decreases with unrest. |
| **체포 경찰** | **Active Cops** | Number of police actively enforcing the law. |
| **조용한 경찰** | **Quiet Cops** | Number of police who stopped arresting due to high risk. |
| **경찰의 위험 회피 평균** | **Avg Cop Risk Aversion** | Average risk aversion of police agents. |
| **경찰의 고난 평균** | **Avg Cop Hardship** | Average hardship felt by police agents. |
| **경찰의 인센티브 평균** | **Avg Cop Incentive** | Incentive to arrest (`L * (1 - Cop Hardship)`). |
| **경찰의 순 위험 평균** | **Avg Cop Net Risk** | Net risk perceived by police when surrounded by rioters. |
| **경찰의 행동결정 공식 평균** | **Avg Cop Decision** | Result of `Incentive - Net Risk`. If low, cops go quiet. |
