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

# Stochastic User Equilibrium (SUE)

