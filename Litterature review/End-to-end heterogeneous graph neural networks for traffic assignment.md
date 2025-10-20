 GNNs are generally constrained to a fixed graph size and 130 often require workarounds-such as transfer learning or padding with dummy nodes, to handle networks of different 131 sizes


# Abstract 

 The paper introduces a new **end-to-end surrogate model** for <span style="color:rgb(255, 0, 0)">solving the <b>user equilibrium traffic assignment problem</b></span> using **heterogeneous graph neural networks (HGNNs)**. Traditional methods struggle with large-scale networks, but this model overcomes those challenges through:

- An **a<span style="color:rgb(255, 0, 0)">daptive graph attention mechanism**</span> combined with **virtual links** connecting origin–destination pairs, allowing better capture of spatial traffic patterns.
    
- Integration of the <span style="color:rgb(255, 0, 0)"><b>node-based flow conservation law</b> into the loss function</span>, ensuring physically consistent prediction


# introduction


 traditional graph models represent only physical road links, lacking direct connections between non-adjacent OD pairs. 
 => In their work they watr to add virtual link between an o d pairs that are not physically connected 

The model introduces several key innovations:

1. A **heterogeneous graph structure** that connects OD nodes through both physical and virtual links, combined with an **adaptive attention mechanism** to model spatial dependencies.
    
2. Integration of **flow conservation laws** into the training process to ensure physically consistent and accurate flow predictions.
    
3. Enhanced **generalization to unseen networks** through the combination of virtual links and conservation-based regularization

# literature

## OD demand estimation

**Origin–destination (OD) demand estimation** is challenging because traffic sensors cannot directly measure travel demand. Researchers therefore infer OD demand from aggregated roadway data using various models. Traditional approaches include **time-series models** such as ARIMA (for forecasting regional demand) and **state estimation techniques** like the **Kalman filter**, as well as **optimization-based methods** such as **quadratic programming** solved via the alternating direction method of multipliers (ADMM).

More recently, **neural networks** have become prominent due to their ability to capture complex spatial–temporal patterns. For example, models combining **graph neural networks with Kalman filters** and **3D convolutional neural networks (CNNs)** have shown improved performance in OD demand prediction. However, **data quality issues**—such as sensor failures or missing data—remain a major challenge, often leading to **inaccurate demand estimation** and subsequent **errors in traffic flow prediction**.

the dqtq thqt ze hqve fro; the OD de;qnd is



