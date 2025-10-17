# UE and SO Objective Function

## Wardrop’s Principles (1952)

Wardrop proposed two fundamental principles to describe traffic assignment behavior:

1. **First Principle – User Equilibrium (UE):**  
   Every traveler seeks to minimize their **own travel cost** (time, money, or generalized cost).  
   At equilibrium, **no traveler can reduce their travel cost by unilaterally changing routes**.  
   - This is analogous to **Nash Equilibrium** in game theory.  
   - All used routes between an origin–destination (OD) pair have **equal and minimal travel costs**.

   Mathematically:  
   If $c_k$ is the cost of route $k$ between OD pair $(r,s)$, then in equilibrium:
   $$
   c_k = c_{rs}^* \quad \text{for all used routes } k,
   $$
   and  
   $$
   c_k \ge c_{rs}^* \quad \text{for all unused routes.}
   $$

2. **Second Principle – System Optimum (SO):**  
   Travelers act **cooperatively** to minimize the **total system cost** (the sum of all users’ travel times or costs).  
   - This represents the **socially optimal** traffic pattern.  
   - Some individuals might take longer routes to improve overall efficiency.



### Comparing UE and SO

| Concept | Objective | Behavior | Result |
|----------|------------|-----------|---------|
| **User Equilibrium (UE)** | Each user minimizes **individual cost** | Selfish behavior | Stable, but possibly inefficient (congestion may persist) |
| **System Optimum (SO)** | Minimize **total system cost** | Cooperative behavior | Efficient but may require coordination or control (e.g., tolls) |



## Understanding the Mathematical Formulation

### Generalized Cost

The **generalized cost** is defined as the normalized sum of *travel*, *waiting*, *service*, and *monetary* costs:

$$
C = \text{Travel Time Cost} + \text{Monetary Cost} + \text{Other Penalties}
$$


### User Equilibrium (UE)

In general, the **travel time** (in case we want the cost of the travel time, we add a the cost factor $\alpha$) on a link for *User Equilibrium* is expressed as:



$$
\min \sum_{a \in A} \int_{0}^{x_a} \alpha \, t_a(w) \, dw
$$

### Interpretation
It’s the **sum of each link’s cost**.

**Notation:**
- $a$: a link  
- $x_a$: flow on link $a$  
- $t_a$: travel time on link $a$  
- $A$: the set of all links  
- $\alpha$: Monetary cost per unit of time (monetary unit/time unit)  



### Travel Time Function

The travel time on each link $a$ can follow:

1. **Bureau of Public Roads (BPR) function:**

   $$
   t_a(x_a) = t_a^0 \left(1 + \alpha \left(\frac{x_a}{c_a}\right)^{\beta}\right)
   $$

   where  
   - $t_a^0$: free-flow travel time  
   - $c_a$: link capacity  
   - $\alpha, \beta$: parameters of the BPR function  

2. **Queue Volume Delay Function (QVDF):**  
   Used when delays are modeled as a function of queue length or volume.




### System Optimum (SO)

For **System Optimum**, the objective minimizes the total *system travel time cost* on each link:

$$
\min \sum_{a \in A} \alpha \, t_a(x_a) \, x_a
$$

###  Summary

| Concept                   | Objective Function                                          | Interpretation                                             |
| ------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------- |
| **User Equilibrium (UE)** | $\min \sum_{a \in A} \int_{0}^{x_a} \alpha \, t_a(w) \, dw$ | Each user minimizes their own cost (selfish behavior).     |
| **System Optimum (SO)**   | $\min \sum_{a \in A} \alpha \, t_a(x_a) \, x_a$             | The total system cost is minimized (cooperative behavior). |

