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
Each traveler’s perceived utility $U_k$ for route \( $k$ \) is modeled as:

$$
U_k = V_k + \varepsilon_k
$$

where:

- $( V_k )$: deterministic (measured) utility: what we can measure, like travel time, cost, comfort, etc   
- $( \varepsilon_k )$: random error term capturing perception differences

A **stochastic equilibrium** is reached when:

> No traveler believes they can improve their perceived travel time by unilaterally changing routes.

When perception variance → 0, SUE becomes equivalent to DUE.


- A **high** UkU_kUk​ means that route _k_ seems more attractive to that traveler.
    
- A **low** UkU_kUk​ means it seems less attractive.
    

When we say “traveler chooses the route with the highest utility,” it means:

> Out of all available routes, the traveler picks the one that gives them the most perceived benefit (or lowest perceived cost/time).

---

## 3. Classical SUE Models (Unbounded Distributions)

Two main SUE formulations arise from different assumptions about \( \varepsilon_k \):

| Model  | Distribution of \( \varepsilon_k \) | Choice Probability                                           |
| ------ | ----------------------------------- | ------------------------------------------------------------ |
| Logit  | Gumbel (IID)                        | $( P_k = \dfrac{e^{V_k / \theta}}{\sum_j e^{V_j / \theta}})$ |
| Probit | Multivariate normal                 | $( P_k = Pr(U_k > U_j, \forall j \neq k) )$                  |

These assume that perception errors are **unbounded**, which implies that:

> Every route has some positive choice probability — even extremely poor routes.

This behavior is unrealistic for real-world networks.

---

