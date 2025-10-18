
## Core Idea

This study introduces a **data-driven approach** to learn **traffic flow patterns** in transportation networks directly from data, ==without assuming user behavior models like user equilibrium or system optimal==.
The method reformulates the traditional **traffic assignment problem** as a **learning task**, using a **Graph Convolutional Neural Network (GCNN)** to model how travel demand from various origins and destinations diffuses through network links.

## Problematic

The **Traffic Assignment Problem (TAP)** is central to transportation planning, traditionally solved using **User Equilibrium (UE)** models that assume perfect driver knowledge and rational route choices. However, these assumptions often fail in real-world, dynamic traffic conditions.

While **Dynamic Traffic Assignment (DTA)** models offer more realism, they are computationally expensive and unsuitable for large-scale, real-time applications.


With the rise of **traffic sensors**, **connected vehicles**, and **big data**, there is growing potential for **data-driven approaches** to estimate and forecast traffic flows. Yet, most existing data-driven models only handle **short-term predictions** on small road segments and fail to capture **network-wide dynamics** or **travel demand variations**.

To address these gaps, this study introduces a **Graph Convolutional Neural Network (GCNN)** framework that learns ***traffic flow patterns** directly from data*—without relying on behavioral assumptions. By representing transportation networks as graphs and modeling the **diffusion of origin-destination (OD) demand** through links.

In this work, they seek to answer the question:
> ==Can a deep learning model learn the flow patterns of a network without relying on the assumptions of user behavior for assigning traffic in the network?==


## DATA-DRIVEN TRAFFIC ASSIGNMENT




- **Transportation network** is represented as a **weighted directed graph**.
- Each link between nodes carries information such as **distance, speed limit, capacity,** and **free-flow travel time**.
- The goal is to learn a **mapping function** that relates **origin-destination (OD) travel demands** to **link flows** in the network using available data and network characteristics (e.g., node locations, travel times).
- 