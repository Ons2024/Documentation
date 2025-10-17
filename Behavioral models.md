# Behavioral Models in Transportation

## What is a Behavioral Model?

A **behavioral model** in transportation describes **how travelers make choices** — such as which **route**, **mode** (car, bus, bike), or **departure time** to use.

It provides a **mathematical representation** of human decision-making by modeling how people **trade off** different factors like:

- **Travel time**
- **Cost or tolls**
- **Comfort or convenience**
- **Reliability or uncertainty**

The **goal** is to capture, in equations, how real travelers behave when faced with multiple alternatives.

---

## The Traditional “Bottom-Up” Approach

In the traditional approach, researchers **pre-select** the model form before calibrating it with data. This means the behavioral rule is **assumed in advance** based on theory or simplicity.

### Process:
1. **Assume a behavioral rule**
   - Example: “Travelers always choose the shortest travel time”  
     or “Choice follows a probabilistic rule depending on perceived utility.”

2. **Select a mathematical model** that expresses this assumption  
   - Common example: the **Multinomial Logit (MNL)** model.

3. **Calibrate model parameters** (e.g., coefficients for time, cost, etc.)  
   - Usually based on **survey data** (stated or revealed preferences), not actual network flows.

### Limitation
This method assumes that the pre-selected behavioral rule is correct.  
In reality, travelers’ true decision-making processes may differ — leading to models that **don’t reproduce observed traffic patterns accurately**.

---

## Example: Multinomial Logit (MNL) Model

The **MNL model** gives the **probability** that a traveler chooses a particular route (or mode) among several alternatives, based on its **utility**.

### Utility Function
The utility of route *i* is expressed as:

$$
U_i = \beta_1 \cdot (\text{travel time}) + \beta_2 \cdot (\text{cost}) + \dots + \varepsilon_i
$$

- $\beta$ parameters capture how strongly travelers value each attribute.  
- $\varepsilon_i$ is a random term accounting for unobserved factors.

### Choice Probability
The probability of choosing route *i* is:

$$
P_i = \frac{e^{U_i}}{\sum_j e^{U_j}}
$$

This means:
- Routes with **shorter travel times** or **lower costs** get **higher probabilities**.  
- The model assumes **independence of irrelevant alternatives (IIA)** — meaning each route’s utility is independent of others (a known limitation).

---

## How It’s Used in Equilibrium Modeling

When integrated into network models, behavioral models like MNL help simulate **how traffic distributes itself** across routes.

1. Probabilities determine **traffic flow on each route**.  
2. These flows influence **travel times** (congestion increases travel time).  
3. The process repeats until an **equilibrium** is reached —  
   where no traveler can improve their travel time by switching routes.  
   
---

## Other Common Behavioral Models

Behavioral models vary in complexity and realism. Here are some key examples:

### 1. **Deterministic Models**
- Travelers **always choose** the option with **minimum travel time or cost**.  
- Example: *Shortest Path Model*.  
- Limitation: Ignores variability in perception or uncertainty.

### 2. **Multinomial Logit (MNL)**
- Probabilistic choice based on **utility** and **IIA** assumption.  
- Simple and widely used.

### 3. **Nested Logit (NL)**
- Extension of MNL that allows **correlation between alternatives** (e.g., routes sharing common links).  
- Captures more realistic substitution patterns.

### 4. **Probit Model**
- Utility errors follow a **normal distribution**, allowing **correlation** among alternatives.  
- More flexible but computationally intensive.

### 5. **Mixed Logit (ML) / Random Parameters Logit**
- Allows model parameters (e.g., $\beta_1, \beta_2$) to **vary across individuals**.  
- Captures **heterogeneity** in traveler preferences.

### 6. **Hybrid Choice Models (HCM)**
- Integrate **psychological factors**, attitudes, and perceptions.  
- Combine traditional discrete choice models with **latent variables**.

---

# 🎲 Stochastic User Equilibrium (SUE)

## Overview

The **Stochastic User Equilibrium (SUE)** extends the classical User Equilibrium (UE) — Path Flow Formulation by recognizing that **travelers do not perceive travel times and costs perfectly**.

In real networks, drivers:
- have **imperfect information** (they don’t know all travel times),
- perceive **uncertainty** (due to congestion, incidents, weather),
- and exhibit **individual variability** in preferences.

Thus, instead of everyone deterministically choosing the *minimum-cost route*, choices are made **probabilistically**, based on **perceived utility**.

---

## Behavioral Foundation

The SUE model is built upon **behavioral choice theory**, specifically the Behavioral Models in Transportation and **Multinomial Logit (MNL)** model.

Each traveler is assumed to choose the route that **maximizes their perceived utility**, but since utility has a random component, the choice is **stochastic**.

The perceived utility of route *i* is:

$$
U_i = V_i + \varepsilon_i
$$

where:
- $V_i$ = deterministic component (usually a function of travel time and cost),
- $\varepsilon_i$ = random error term representing perception error or unobserved factors.

---

##  Choice Probability (Multinomial Logit Form)

If the random terms $\varepsilon_i$ are independently and identically distributed (Gumbel type I), then the **probability** that route *i* is chosen is given by the **Multinomial Logit (MNL)** formula:

$$
P_i = \frac{e^{\theta V_i}}{\sum_{j \in C_r} e^{\theta V_j}}
$$

where:
- $\theta$ = dispersion (scale) parameter that captures the **degree of randomness** in perception:
  - Large $\theta$ → small randomness → approaches deterministic UE.  
  - Small $\theta$ → large randomness → choices become more random.
- $C_r$ = set of available routes between origin–destination pair *r*.

---

## ⚙️ Mathematical Formulation of SUE

The **SUE condition** states that, at equilibrium, **no traveler can improve their perceived utility** by changing routes — in expectation.

Let:
- $x_a$ = flow on link *a*,  
- $t_a(x_a)$ = travel time on link *a*,  
- $P_{p}^{r}$ = probability of choosing path *p* for OD pair *r*.

Then the flow on path *p* is:

$$
f_{p}^{r} = q_r \cdot P_{p}^{r}
$$

where $q_r$ is the total demand between OD pair *r*.

The equilibrium condition is reached when these perceived costs are consistent with the resulting flows and travel times.

---




