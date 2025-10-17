## The Equilibrium Assignment and the Beckmann Problem

The **equilibrium assignment problem** in traffic modeling is **essentially equivalent** to the **Beckmann problem**.  
Beckmann, McGuire, and Winsten (1956) showed that **Wardrop’s First Principle** (User Equilibrium) can be expressed as a **convex optimization problem**—now known as the *Beckmann formulation*.

---

### Conceptual Link
[[]]
- **Wardrop’s User Equilibrium (UE):**
  > No traveler can reduce their travel cost by unilaterally changing routes.

- **Beckmann’s Contribution:**
  > Showed that the set of flows satisfying Wardrop’s UE conditions is the solution to a **convex minimization problem**.

Mathematically, this is represented as:

$$
\min_{x} \; Z(x) = \sum_{a \in A} \int_0^{x_a} t_a(w) \, dw
$$

subject to:

$$
\sum_{k\in K_{rs}} f_k^{rs} = q_{rs}, \qquad 
f_k^{rs} \ge 0, \qquad
x_a = \sum_{r,s} \sum_{k\in K_{rs}} \delta_{a k}^{rs} f_k^{rs}
$$

---

### Convexity of the Beckmann Problem

The **Beckmann problem is convex**, which guarantees that:

- There exists a **unique** set of equilibrium link flows (though multiple path-flow combinations may correspond to it).
- The optimization can be solved using efficient convex optimization algorithms.

---

#### Why It’s Convex

1. **Objective Function Convexity:**

   Each link’s travel time function $t_a(x_a)$ is assumed to be **continuous and non-decreasing** (e.g., the BPR function):

   $$
   t_a(x_a) = t_a^0 \left[ 1 + \alpha \left( \frac{x_a}{c_a} \right)^\beta \right]
   $$

   Because $t_a(x_a)$ is non-decreasing, its integral   $\displaystyle \int_0^{x_a} t_a(w)\,dw$  is **convex** in $x_a$.
   Therefore, the total objective:
   $$
   Z(x) = \sum_{a\in A} \int_0^{x_a} t_a(w)\,dw
   $$
   is **convex**.

2. **Constraints are Linear:**
   - Flow conservation:
     $$
     \sum_{k\in K_{rs}} f_k^{rs} = q_{rs}
     $$
   - Nonnegativity:
     $$
     f_k^{rs} \ge 0
     $$
   - Link–path incidence:
     $$
     x_a = \sum_{r,s}\sum_{k\in K_{rs}} \delta_{a k}^{rs} f_k^{rs}
     $$

   Linear constraints preserve convexity of the feasible set.

---

### Implications

| Property | Meaning |
|-----------|----------|
| **Convexity** | Guarantees global optimality — no local minima. |
| **Continuity** | Ensures existence of equilibrium. |
| **Monotonicity of $t_a(x_a)$** | Prevents oscillatory or unstable flow patterns. |
| **Equivalence to Wardrop UE** | The solution to the Beckmann problem satisfies Wardrop’s first principle. |

---

###  Summary

> The **Equilibrium Assignment Problem** is simply the **Beckmann optimization problem** applied to transportation networks.  
> It provides a mathematical bridge between **individual route choice behavior** (Wardrop) and **system-level flow equilibrium** (convex optimization).

---

###  Reference

Beckmann, M.J., McGuire, C.B., & Winsten, C.B. (1956).  
*Studies in the Economics of Transportation.*  
Yale University Press, New Haven.
