# From Civil Violence to Regime Overthrow (ABM)
**Extending Epstein's Model: Simulating the Dynamics of Regime Change using NetLogo**

This project extends Epstein's (2002) classic *Civil Violence Model*. While the original model explains sporadic outbursts of violence, this project introduces new variables—**Information Diffusion, Dynamic Legitimacy, and Active Police Agents**—to simulate the mechanism of long-term **Regime Overthrow**.

---

## 📂 Repository Structure

### 1. Model Source Codes
Click the links below to view the NetLogo source code for each stage.

* **Baseline Model:** [📄 Rebellion_netlogo original code.nlogo](./Rebellion_netlogo%20original%20code.nlogo)
    * *Replication of Epstein's original Model IV.*
* **Modified Model I (Spread):** [📄 Modified Rebellion 1_Probability of spread and Probability of jump.nlogo](./Modified%20Rebellion%201_Probability%20of%20spread%20and%20Probability%20of%20jump.nlogo)
    * *Implements Neighbor Effects & Information Diffusion.*
* **Modified Model II (Final):** [📄 Modified Rebellion 2_Legitimacy feedback and Cops go quiet.nlogo](./Modified%20Rebellion%202_Legitimacy%20feedback%20and%20Cops%20go%20quiet.nlogo)
    * *Implements Dynamic Legitimacy & Rational Police Agents (Regime Overthrow).*

### 2. Simulation Data & References
* **Simulation Results:** [📂 View Data Files (Excel)](./results/)
* **Reference Paper:** [📄 Reference_Paper_In KOREAN.pdf](./Reference_Paper_In%20KOREAN.pdf)

---

## 💻 Key Logic & Algorithms

This simulation introduces three key algorithmic extensions to the original Epstein model.

### A. Neighbor & Information Spread (Stage 1)
Unlike the random activation in the original model, this logic allows rebellion to spread contagiously through neighbors and random information jumps.

**1. Spread Activation (Neighbor Effect)**
Agents are influenced by their immediate neighbors. If a neighbor is rebellious, the agent has a probability of joining the rebellion.

```netlogo
to spread-activation
  ; Check if neighbor activation is enabled and probability met
  if neighbors-activation? and random 100 < probability-of-spread [
    ; Identify inactive neighbors around active agents
    let inactive-neighbors neighbors4 with [ any? agents-here and [not active?] of one-of agents-here ]
    
    ask inactive-neighbors [
      ask agents-here [
        ; Attempt to activate the neighbor based on probability
        if not active? and random 100 < probability-of-spread [
          set active? true
          set total-spread-activation total-spread-activation + 1
        ]
      ]
    ]
  ]
end
```

**2. Random Jump (Information Diffusion) Information about the rebellion can travel to random agents anywhere on the grid, simulating media or word-of-mouth.**
```netlogo
to random-jump-activation
  if jump-activation? and random 100 < probability-of-jump [
    ; Pick a random inactive agent regardless of location
    let inactive-agent one-of agents with [ not active? and jail-term = 0 ]
    if inactive-agent != nobody [
      ask inactive-agent [
        set active? true  ; The agent becomes active
        set total-random-jump-activation total-random-jump-activation + 1
      ]
    ]
  ]
end
```

###B. Dynamic Legitimacy Feedback (Stage 2)
In the original model, legitimacy is fixed. Here, government legitimacy (L) decreases dynamically as the number of jailed citizens and rioters increases.

``` netlogo
to update-legitimacy
  let jailed-count count agents with [jail-term > 0]
  let rebellious-count count agents with [ active? ]
  
  if count agents > 0 [
    ; Legitimacy decreases proportional to social unrest
    set government-legitimacy max (list 0 (government-legitimacy - 0.001 * ((jailed-count / count agents) + (rebellious-count / count agents))))
  ]
end
C. Rational Police Agents & Regime Collapse (Stage 2)
Police agents act rationally based on incentives and risks. If they are overwhelmed by rioters, they stop arresting (quiet? becomes true), which simulates the collapse of state authority.


```
**1. Calculate Risk & Incentive**

```
to calculate-incentive-and-risk
  ; Incentive decreases as Legitimacy drops
  set incentive* government-legitimacy * (1 - perceived-hardship*)

  ; Risk increases if rioters outnumber cops (Probability Overwhelmed)
  let a_c count agents-on neighborhood
  let c_c 1 + count (cops-on neighborhood) with [ incentive* - net-risk* > threshold ]
  set probability-overwhelmed* 1 - exp (- k * floor (a_c / c_c))

  ; Net Risk calculation
  set net-risk* risk-aversion* * probability-overwhelmed*
end
```

**2. Enforce or Go Quiet**

```to enforce
  calculate-incentive-and-risk

  ; If the incentive to arrest is higher than the risk, enforce the law
  ifelse incentive* - net-risk* > threshold [
    set quiet? false
    ; Proceed with arrest logic...
    if any? (agents-on neighborhood) with [ active? ] [
       let suspect one-of (agents-on neighborhood) with [ active? ]
       move-to suspect
       ask suspect [ set active? false set jail-term random max-jail-term ]
    ]
  ]
  [
    ; If risk is too high, the cop goes quiet (stops arresting)
    set quiet? true
  ]
end
```

📊 Simulation Results & Findings
Original Model: Shows random, sporadic riots that are quickly suppressed. The regime remains stable.

Modified Model: Incorporating dynamic legitimacy and active police agents creates a "Tipping Point".

Once the rebellion reaches a critical mass, police stop enforcing the law (quiet? status).

This leads to a sustained, massive rebellion, effectively simulating a Regime Overthrow.

