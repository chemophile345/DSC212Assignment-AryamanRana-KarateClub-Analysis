# DSC212Assignment-AryamanRana-KarateClub-Analysis

# Modularity on the Karate Club Graph 🥋  
**Course:** DSC212 
**Author:** Aryaman Rana  (IMS24278)
**Institution:** IISER TVM

---

## Overview
This repository contains a full implementation of **spectral modularity-based community detection** on the **Zachary Karate Club network**, a classic benchmark in network science.  
The project applies **Newman’s spectral modularity method** to uncover community structure and analyze network metrics such as **degree, betweenness, closeness, and clustering centralities** through **recursive bipartitioning**.

The notebook explores how mathematical modularity maximization aligns with real-world social divisions, reproducing the famous **“Mr. Hi vs. John A” split** observed in the original dataset.

---

##  Objectives
1. Understand modularity as a **quality function** for community detection.  
2. Implement **spectral modularity bipartition** using the leading eigenvector of the modularity matrix.  
3. Extend to **multi-community detection** via recursive bisection.  
4. Visualize community evolution and **track network metrics** at each split.  
5. Compare detected communities to **ground truth** and analyze accuracy.  

---

##  Theoretical Background

### Modularity Matrix
For an undirected graph \( G(V, E) \):
\[
B = A - \frac{k k^T}{2m}
\]
where:
- \(A\) = adjacency matrix  
- \(k_i\) = degree of node *i*  
- \(m\) = total number of edges  

The modularity for a partition vector \( s \in \{-1, +1\}^n \) is:
\[
Q = \frac{1}{4m} s^T B s
\]

Maximizing \( Q \) is NP-hard, so we **relax** \( s \) to real values and use the **leading eigenvector** of \(B\) to find a near-optimal split.

---

## Implementation Details

### Main Steps
1. **Compute the modularity matrix \(B\)** for the full graph.  
2. **Find the leading eigenvector** and eigenvalue of \(B\).  
3. **Split the graph** into two communities based on the sign of the eigenvector components.  
4. **Check the eigenvalue criterion**:
   - If λ₁ > 0 → split is meaningful.  
   - If λ₁ ≤ 0 → no further split improves modularity.  
5. **Recursively repeat** for each sub-community (recursive bisection).  

---

##  Features Implemented
✅ Recursive spectral modularity bipartition  
✅ Visualizations after each split (colored communities)  
✅ Computation of:
- Degree centrality  
- Betweenness centrality  
- Closeness centrality  
- Clustering coefficient  

✅ Metric evolution tracking across iterations  
✅ Community quality metrics (density, conductance, average degree)  
✅ Comparison with **ground truth faction split**  
✅ Automated **analysis and insights summary**  

---

##  Outputs & Visualizations
- **Network graphs** with nodes colored by community at each iteration.  
- **Metric evolution plots** showing how centrality measures change over splits.  
- **Community size evolution** across iterations.  
- **Comparison plots** between detected and true (Mr. Hi vs John A) communities.  

---

##  Key Results
- The algorithm correctly identifies the **two main factions** in the Karate Club.  
- **Mr. Hi (Node 0)** and **John A (Node 33)** remain the most central across all iterations.  
- **Betweenness centrality** peaks for bridge nodes (e.g., Node 2).  
- **Clustering coefficients** rise within tightly-knit communities.  
- Final modularity ≈ *0.38–0.40*, aligning with published results.  
- Accuracy vs. ground truth > **90%** (pairwise agreement).  


##  Repository Structure
