# Stochastic User Equilibrium (SUE) and the eUnit-SUE Model

## 1. Background: User Equilibrium (UE)

Deterministic User Equilibrium (DUE) assumes that:

- Every traveler knows the exact travel times on all routes.  
- All travelers behave identically and rationally.  
- At equilibrium, no traveler can improve their travel time by switching routes.

Mathematically:

$$
t_r(f_r) = \min_{p \in P_{od}} t_p(f_p)
$$

for all used routes \( r \) between each origin–destination (O–D) pair.

**Interpretation:**  
All used routes have equal (minimum) travel times; unused routes have higher times.

---

## 2. Stochastic User Equilibrium (SUE)

In reality, travelers:

- Do not have perfect information,  
- May perceive travel times differently, and  
- Therefore may not all choose the same “shortest” route.

In SUE models:

Each route’s perceived travel time is treated as a random variable.  
Each traveler’s perceived utility \( U_k \) for route \( k \) is modeled as:

$$
U_k = V_k + \varepsilon_k
$$

where:

- ( \V_k\ ): deterministic (measured) utility (e.g., – travel time)  
- \( \varepsilon_k \): random error term capturing perception differences

A **stochastic equilibrium** is reached when:

> No traveler believes they can improve their perceived travel time by unilaterally changing routes.

When perception variance → 0, SUE becomes equivalent to DUE.

---

## 3. Classical SUE Models (Unbounded Distributions)

Two main SUE formulations arise from different assumptions about \( \varepsilon_k \):

| Model | Distribution of \( \varepsilon_k \) | Choice Probability |
|--------|-------------------------------------|--------------------|
| Logit | Gumbel (IID) | \( P_k = \dfrac{e^{V_k / \theta}}{\sum_j e^{V_j / \theta}} \) |
| Probit | Multivariate normal | \( P_k = Pr(U_k > U_j, \forall j \neq k) \) |

These assume that perception errors are **unbounded**, which implies that:

> Every route has some positive choice probability — even extremely poor routes.

This behavior is unrealistic for real-world networks.

---

## 4. The eUnit-SUE Model: Bounded Perceptions

The **eUnit-SUE (Exponentiated Uniform)** model overcomes this limitation.

- It assumes the random error \( \varepsilon_k \) follows a **bounded uniform distribution** between \([a, b]\).  
- The model fits within the **Exponentiated Random Utility Maximization (ERUM)** framework.

### Key Properties

- Bounded support: perception differences are limited → more realistic behavior  
- Endogenous bounds: lower and upper limits depend on network conditions  
- Closed-form solution: allows analytical computation of choice probabilities  
- Beckmann-type formulation: enables mathematical programming representation with existence, uniqueness, and equivalence proofs

### Behavioral Insights

- Larger bound range → higher perception variability → more routes receive nonzero flow  
- Smaller bound range → travelers behave more deterministically → flows approach DUE  
- Misperception depends on:
  - The difference between shortest and longest travel times  
  - The width of the bound range

---

## 5. Mathematical Summary

If perceived utility is:

$$
U_k = V_k + \varepsilon_k, \quad \varepsilon_k \sim \text{Uniform}(a,b)
$$

Then the probability of choosing route \( k \) is:

$$
P_k = Pr(U_k > U_j, \forall j \neq k)
$$

This leads to a **bounded**, **closed-form** choice probability — unlike logit or probit, where tails are infinite.

---

## 6. Comparison of Equilibrium Models

| Feature | DUE | SUE (Logit/Probit) | eUnit-SUE |
|----------|-----|--------------------|------------|
| Perception error | None | Unbounded (Gumbel/Normal) | Bounded (Uniform) |
| Choice probability | 0 or 1 (deterministic) | Always > 0 | Zero for very poor routes |
| Flow dispersion | None | Moderate | Controlled by bound width |
| Behavioral realism | Low | Moderate | High |

---

## 7. Numerical and Conceptual Insights

- As the bound width increases, flow dispersion increases (more diverse route use).  
- As the bound width decreases, flow concentrates on the shortest route (approaching DUE).  
- The eUnit-SUE model bridges the gap between deterministic and stochastic equilibria, achieving both realism and tractability.
