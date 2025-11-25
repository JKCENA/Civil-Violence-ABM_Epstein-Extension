# 📊 Simulation Result Tables (PDF)

This directory contains the detailed statistical outcomes of the NetLogo simulations in PDF format. The data includes descriptive statistics (Mean, Standard Deviation, Min, Max) for key variables such as the number of rioters, police behavior, and government legitimacy.

## 📂 File Descriptions

### 1. Main Paper Results
* **File:** [📄 Regime_Overthrow_Result_Tables.pdf](./Regime_Overthrow_Result_Tables.pdf)
* **Description:** This file contains the **key result tables** that were selected and organized for the research paper.
* **Contents:**
    * **Table 1:** Descriptive Statistics of the original Epstein Model (Baseline).
    * **Table 2-4:** Results from the **Neighbor Diffusion Model** (Sensitivity analysis on diffusion probability).
    * **Table 5-7:** Results from the **Information Jump Model**.
    * **Table 8:** Results from the combined **Diffusion & Jump Model**.
    * **Table 9:** Statistics of the final **Regime Overthrow Model** (Dynamic Legitimacy & Police Behavior).
    * **Table 10:** Comparison of the **Mean Cycle of Riots** across different models.

### 2. Supplementary Results
* **File:** [📄 Other_Results_not_included_in_Paper_Tables.pdf](./Other_Results_not_included_in_Paper_Tables.pdf)
* **Description:** This file contains **additional experimental data** and sensitivity analyses that were conducted during the research but were not included in the final paper due to space constraints.
* **Contents:**
    * Extensive sensitivity analysis on **Political Oppression Levels** (Levels 4, 5, 6).
    * Experiments on specific scenarios: **Rebellion Expansion, Riot Duration, Riot Repetition**, and cases with **No Riots**.
    * Detailed breakdown of **Neighbor vs. Jump effects** with various probability combinations (e.g., Neighbor 5 / Jump 10, etc.).
    * Analysis of specific phases like the "Start Point of Riot Persistence".

---

## 📝 Metric Definitions
Both PDF files report the following metrics for each simulation run:

| Metric | Description |
| :--- | :--- |
| **Rioting / Quiet / Jailed Citizens** | Counts of citizen agents in each state. |
| **Arresting / Quiet Police** | Counts of active vs. inactive police agents. |
| **Mean Risk Aversion (C/P)** | Average risk aversion for Citizens (C) and Police (P). |
| **Mean Net Risk (C/P)** | The calculated net risk perceived by agents. |
| **Gov. Legitimacy Feedback** | The dynamic level of government legitimacy (Model II only). |
