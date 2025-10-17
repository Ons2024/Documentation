# UE and SO Objective Function

## Understanding the Mathematical Formulation



### 1. Generalized Cost

The **generalized cost** is defined as the normalized sum of *travel*, *waiting*, *service*, and *monetary* costs:

$$
C = \text{Travel Time Cost} + \text{Monetary Cost} + \text{Other Penalties}
$$



## User Equilibrium (UE)

In general, the **travel time** (in case we cannot directly measure travel time, we add a weight factor $ \alpha $ on a **link** for *User Equilibrium* is expressed as:


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
- $ \alpha $ 



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



### Full User Equilibrium Objective

$$
\min Z_{UE} = 
\sum_{n \in N} \sum_{a \in A_n} \int_0^{x_a} \alpha \, t_{a,n}(\omega) \, d\omega 
+ 
\sum_{a \in A} \sum_{m \in \Psi} 
\left[\alpha (WT_{m,a} + ST_{m,a}) + C_{m,a}\right] \, x_{a,m}
$$

where  
- $WT_{m,a}$: waiting time on mode $m$, link $a$  
- $ST_{m,a}$: service time  
- $C_{m,a}$: monetary cost  
- $N$: set of all users or OD pairs  
- $\Psi$: set of available modes  



## System Optimum (SO)

For **System Optimum**, the objective minimizes the total *system travel time cost* on each link:

$$
\min \sum_{a \in A} \alpha \, t_a(x_a) \, x_a
$$

Or equivalently:

$$
\min Z_{SO} =
\sum_{n \in N} \sum_{a \in A_n} \alpha \, t_{a,n}(x_a) \, x_a 
+ 
\sum_{a \in A} \sum_{m \in \Psi} 
\left[\alpha (WT_{m,a} + ST_{m,a}) + C_{m,a}\right] \, x_{a,m}
$$



##  Summary


| Concept                   | Objective Function                                          | Interpretation                                             |
| ------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------- |
| **User Equilibrium (UE)** | $\min \sum_{a \in A} \int_{0}^{x_a} \alpha \, t_a(w) \, dw$ | Each user minimizes their own cost (selfish behavior).     |
| **System Optimum (SO)**   | $\min \sum_{a \in A} \alpha \, t_a(x_a) \, x_a$             | The total system cost is minimized (cooperative behavior). |

---

**Key Idea:**  
UE corresponds to *Wardrop’s First Principle* (**individual optimization**),  
while SO corresponds to *Wardrop’s Second Principle* (**system optimization**).