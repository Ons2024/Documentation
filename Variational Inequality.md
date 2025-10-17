# Variational Inequality (VI) in Traffic Assignment

## Concept Overview

The **Variational Inequality (VI)** formulation provides a **unified mathematical framework** to express *equilibrium conditions* — including **User Equilibrium (UE)** and **Stochastic User Equilibrium (SUE)**.

It is particularly useful when the relationship between **link flows** and **travel costs** is nonlinear and cannot easily be expressed as an optimization problem.

---

##  Basic Idea

Let:
- $mathcal{F}$ : the set of **feasible flow vectors** (flows that satisfy demand conservation)
- $c(x)$: the **link (or route) cost vector** as a function of the flow $x$

Then the **variational inequality problem**  ${VI}(c, \mathcal{F})$  is to find a flow vector  $x^*$ in $mathcal{F}$ such that:

$$
\langle c(x^*), \, x - x^* \rangle \ge 0, \quad \forall x \in \mathcal{F}
$$

or equivalently:

$$
\sum_{a} c_a(x^*) \, (x_a - x_a^*) \ge 0, \quad \forall x \in \mathcal{F}
$$

where:
- $c_a(x^*)$: travel cost on link \( a \) under equilibrium flow $x^* $
- $langle \cdot, \cdot \rangle$: inner product
- $mathcal{F}$: feasible set of flows that meet all OD demand constraints

---

##  Interpretation (Traffic Context)

At **equilibrium**, no traveler can improve their travel cost (or perceived utility) by unilaterally changing routes.  
This means the current flow pattern \( $x^*$ satisfies the VI condition — i.e., any feasible deviation $x - x^*$ cannot *decrease* total travel cost.

---

## Connection to User Equilibrium (UE)

The **Deterministic User Equilibrium (DUE)** (Wardrop’s first principle) states:

> “All used routes between an origin and destination have equal and minimal travel times.”

This condition can be expressed as a VI problem:

$$
\text{Find } x^* \in \mathcal{F} \text{ such that } 
\sum_{a} c_a(x^*) (x_a - x_a^*) \ge 0, \quad \forall x \in \mathcal{F}
$$

If the cost function \( c(x) \) is **monotone** (i.e., increasing with flow), this VI has a **unique** solution.

---

## Connection to Stochastic User Equilibrium (SUE)

In **SUE**, travelers perceive route costs **with randomness**.  
Each route has a **choice probability** $P_k$ depending on its perceived utility.

Even though the choice process is probabilistic, the equilibrium condition can *also* be written as a **variational inequality**:

$$
\sum_{k} \bar{c}_k(f^*) \, (f_k - f_k^*) \ge 0, \quad \forall f \in \mathcal{F}
$$

where:
- $f_k^*$: equilibrium route flow  
- $bar{c}_k(f^*)$: **expected perceived cost** on route  $k$ 

Thus, both UE and SUE share the **same VI structure**, but differ in how  $c_k$  is defined:
- For **UE** → actual travel cost  
- For **SUE** → perceived (expected) cost

---

##  Relation to Optimization

If \( c(x) \) derives from a potential function \( Z(x) \):

$$
c(x) = \nabla Z(x)
$$

then the VI condition is **equivalent** to the optimization problem:

$$
\min_{x \in \mathcal{F}} Z(x)
$$

This happens in **Beckmann’s formulation** for the UE problem, where:

$$
Z(x) = \sum_a \int_0^{x_a} c_a(w) \, dw
$$

---

##  Properties

| Property | Description |
|-----------|--------------|
| **Existence** | A solution exists if \( c(x) \) is continuous and \( \mathcal{F} \) is compact. |
| **Uniqueness** | Guaranteed if \( c(x) \) is strictly monotone. |
| **Interpretation** | At \( x^* \), all feasible deviations increase total perceived cost. |
| **Numerical Solvers** | Projection methods, Frank–Wolfe, and extra-gradient algorithms are often used. |

---

##  Geometric Intuition

The VI condition means:
- The **cost vector** \( c(x^*) \) forms an **acute angle** with every feasible direction \( (x - x^*) \).
- Therefore, any move away from \( x^* \) would **increase** total travel cost.

Visually, \( x^* \) lies at a point where the feasible region \( \mathcal{F} \) and the cost vector \( c(x^*) \) “touch” without allowing any improving direction.

---

##  Summary

| Concept | UE | SUE | VI Representation |
|----------|----|-----|-------------------|
| Traveler Behavior | Perfect perception | Random perception | \( \sum c(x^*)(x - x^*) \ge 0 \) |
| Cost Type | Actual travel time | Expected perceived cost | Same VI form |
| Deterministic? | ✅ Yes | ❌ No | Unified framework |
| Equivalent Optimization? | ✅ (Beckmann) | Sometimes (e.g., eUnit-SUE) | General case |

