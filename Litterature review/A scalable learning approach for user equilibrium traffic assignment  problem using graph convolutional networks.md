

The paper addresses the **User Equilibrium Traffic Assignment Problem (UE-TAP)** — determining how traffic distributes across a network when every traveler chooses the route that <font color="#c00000">minimizes their travel time</font>. Traditional iterative optimization algorithms for this task are **computationally expensive and inflexible**, especially for large or dynamic networks.

The authors propose a **Graph Convolutional Network (GCN)-based deep learning framework** to directly learn the mapping between **origin–destination (OD) demands** and **equilibrium traffic flows**, <u><font color="#c00000">bypassing the need for iterative solvers</font></u>

---

<span style="color:rgb(255, 255, 0)">The UE traffic assignment problem (UE-TAP) can be formulated as a convex nonlinear program  and solved by the Frank-Wolfe algorithm</span>
However, owing to the classical method’s high complexity and limited efficiency, three main streams of solution algorithms have emerged: <span style="color:rgb(0, 176, 80)">link-based algorithms</span> , <span style="color:rgb(0, 176, 80)">bush-based methods</span> , and <span style="color:rgb(0, 176, 80)">path-based algorithms</span>. More recently,<span style="color:rgb(0, 176, 80)"> parallel computing strategies</span> have been explored to enhance both efficiency and scalability in solving UE-TAP
There is also <span style="color:rgb(0, 176, 80)">data-driven deep learning methods</span> (based on ML and data-driven based)

they develop an end-to-end learning-based framework for user equilibrium prediction under variable network topologies

This study utilizes network partitioning and subgraph training, explicitly incorporating network attributes such as free-flow travel time and link capacity, and employing a variable adjacency matrix as input, thereby making the model adapt dynamically to varying network topologies and significantly improving model robustness.
