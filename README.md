# 🏛️ From Civil Violence to Regime Overthrow
**An Agent-Based Modeling (ABM) Approach using NetLogo**

![NetLogo Badge](https://img.shields.io/badge/NetLogo-6.x-red) ![License Badge](https://img.shields.io/badge/License-MIT-blue)

> **"What turns a riot into a revolution?"**
> This project extends Joshua M. Epstein's (2002) classic civil violence model to simulate the dynamics of **Regime Overthrow**, incorporating factors like information diffusion, dynamic legitimacy, and active police behavior.

---

## 📌 Project Overview

Traditional models often explain civil violence as sporadic outbursts that are quickly suppressed. However, historical events show that resistance can evolve into sustained revolutions.

This project implements a multi-stage simulation in **NetLogo** to explore:
1.  **Spread:** How rebellion spreads via neighbor interactions and global information jumps.
2.  **Tipping Point:** How falling government legitimacy and overwhelmed police forces lead to a sudden regime collapse.

---

## 📂 Repository Structure

This repository is organized into three main sections. Click the links below to navigate.

### 1. [💻 Model Source Code](./Model)
Contains the **NetLogo source codes (`.nlogo`)** for each stage of the simulation.
* **Original Model:** Epstein's baseline model.
* **Modified I:** Incorporating Neighbor Spread & Information Jump.
* **Modified II (Final):** Incorporating Dynamic Legitimacy & Cops Go Quiet.

### 2. [📊 Results & Analysis](./Results)
Contains the **simulation outcome reports (PDF)** and summary tables.
* **Key Findings:** Analysis of the "Tipping Point" and regime collapse scenarios.
* **Comparative Statistics:** Differences between the original and modified models.

### 3. [📈 Raw Simulation Data](./Simulation%20Data)
Contains the **raw dataset (Excel)** exported from the simulations for detailed analysis.

---

## 🔍 Key Features & Logic

| Feature | Original Model (Epstein) | **This Project (Extended)** |
| :--- | :--- | :--- |
| **Legitimacy** | Fixed Constant | **Dynamic** (Drops as arrests/riots increase) |
| **Police Behavior** | Always Arrests | **Rational** (Stops arresting if risk is too high) |
| **Information** | Random Activation | **Network Diffusion** (Neighbor + Jump) |
| **Outcome** | Sporadic Riots | **Regime Overthrow (Sustained)** |

---

## 🚀 How to Run the Simulation

1.  **Download NetLogo:** Ensure you have [NetLogo 6.x](https://ccl.northwestern.edu/netlogo/) installed.
2.  **Clone/Download:** Clone this repository or download the ZIP file.
3.  **Open Model:** Go to the `Model` folder and open `Modified Rebellion 2_Legitimacy feedback and Cops go quiet.nlogo`.
4.  **Setup & Go:**
    * Click the **`Setup`** button to initialize agents.
    * Click the **`Go`** button to start the simulation.
    * Watch the *Government Legitimacy* graph and observe the police behavior (Yellow = Quiet).

---

## 📚 Reference
* **Original Paper:** Epstein, J. M. (2002). "Modeling Civil Violence: An Agent-Based Computational Approach". *Proceedings of the National Academy of Sciences*.
* **Implemented Research:** [📄 Reference Paper (Korean)](./Reference_Paper_In%20KOREAN.pdf)

---

## 👤 Author
* **Develop & Research:** [JI HUN KANG/JKCENA]
* **Contact:** [jihun9965@gmail.com]

*Licensed under the MIT License.*
