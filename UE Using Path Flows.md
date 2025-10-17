## User Equilibrium (UE) — Path Flow Formulation

### Overview

The **User Equilibrium (UE)** principle, introduced by _Wardrop (1952)_, states that:

> In equilibrium, no driver can reduce their travel cost by unilaterally changing routes.

In other words, all **used paths** between any origin–destination (OD) pair have **equal and minimal costs**, while **unused paths** have **equal or higher costs**.

This represents **selfish route choice** behavior — each user independently minimizes their own travel time or cost.

---

### 🔹 Mathematical Representation

At equilibrium, the **path-based UE condition** is expressed as:

fpr,z⋅(cpr,z−urz)=0f_p^{r,z} \cdot (c_p^{r,z} - u_r^{z}) = 0fpr,z​⋅(cpr,z​−urz​)=0

where:

- $f_p^{r,z}$ = flow on path $p$ for OD pair $r$ and user class $z$
    
- $c_p^{r,z}$ = travel cost (or time) on path $p$
    
- $u_r^{z}$ = minimum (shortest) cost between OD pair $(r,z)$
    

**Interpretation:**

- If $f_p^{r,z} > 0$, then $c_p^{r,z} = u_r^{z}$ → path is used and minimal.
    
- If $c_p^{r,z} > u_r^{z}$, then $f_p^{r,z} = 0$ → path is unused (costlier).
    

---

### ⚙️ Full Formulation

fpr,z⋅(cpr,z−urz)=0,∀p∈Pr,∀(r,z)cpr,z−urz≥0,∀p∈Pr,∀(r,z)∑p∈Prfpr,z=xrz,∀(r,z)(Flow conservation)fpr,z≥0,  cpr,z≥0,  urz≥0(Nonnegativity constraints)\begin{aligned} & f_p^{r,z} \cdot (c_p^{r,z} - u_r^{z}) = 0, && \forall p \in P_r, \forall (r,z) \\ & c_p^{r,z} - u_r^{z} \ge 0, && \forall p \in P_r, \forall (r,z) \\ & \sum_{p \in P_r} f_p^{r,z} = x_r^{z}, && \forall (r,z) \quad \text{(Flow conservation)} \\ & f_p^{r,z} \ge 0, \; c_p^{r,z} \ge 0, \; u_r^{z} \ge 0 && \text{(Nonnegativity constraints)} \end{aligned}​fpr,z​⋅(cpr,z​−urz​)=0,cpr,z​−urz​≥0,p∈Pr​∑​fpr,z​=xrz​,fpr,z​≥0,cpr,z​≥0,urz​≥0​​∀p∈Pr​,∀(r,z)∀p∈Pr​,∀(r,z)∀(r,z)(Flow conservation)(Nonnegativity constraints)​

---

### 🔸 Path Cost Definition

Each path cost is the sum of its link costs:

cpr,z=∑e∈EΔp,e(r) cezc_p^{r,z} = \sum_{e \in E} \Delta_{p,e}^{(r)} \, c_e^{z}cpr,z​=e∈E∑​Δp,e(r)​cez​

where:

- $\Delta_{p,e}^{(r)} = 1$ if link $e$ is on path $p$, else $0$.
    
- $E$: set of all links.
    

The minimum cost for OD pair $(r,z)$ is:

urz=min⁡p∈Prcpr,zu_r^{z} = \min_{p \in P_r} c_p^{r,z}urz​=p∈Pr​min​cpr,z​

---

### 🧠 Behavioral Interpretation

- At equilibrium: $c_p^{r,z} = u_r^{z}$ for all used paths.
    
- For unused paths: $c_p^{r,z} > u_r^{z} \Rightarrow f_p^{r,z} = 0$.
    

If the network is **not at equilibrium**, travelers will continue switching to cheaper paths until this condition is satisfied.

This reflects **rational, selfish driver behavior** under Wardrop’s first principle.

---

### 🔗 Relationship to Beckmann’s Formulation

The **[[Beckmann Formulation]]** provides an equivalent _optimization-based representation_ of this equilibrium:

min⁡∑a∈A∫0xata(w) dw\min \sum_{a \in A} \int_0^{x_a} t_a(w)\, dwmina∈A∑​∫0xa​​ta​(w)dw

subject to:

- flow conservation,
    
- nonnegativity.
    

This problem is **convex**, and its optimality conditions are equivalent to the UE complementarity system above.

For comparison, see also your note:  
→ [[UE and SO Objective Function]]