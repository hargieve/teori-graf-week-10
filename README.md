# 🧮 Hungarian Algorithm & Welsh–Powell Algorithm

## 📘 Overview

This project demonstrates two important algorithms in combinatorial optimization and graph theory:

1. 🇭🇺 **Hungarian Algorithm** — used to solve the *Assignment Problem* (minimizing total cost)  
2. 🎨 **Welsh–Powell Algorithm** — used for *Graph Coloring* (minimizing number of colors)

Both algorithms are implemented in Python, with detailed examples and explanations.

---

## 🇭🇺 1. Hungarian Algorithm

### 🎯 Purpose
The **Hungarian Algorithm** (also known as the *Kuhn–Munkres Algorithm*) solves the **Assignment Problem** — assigning `n` workers to `n` tasks so that the total cost is minimized.

---

### ⚙️ Python Code
```python
from scipy.optimize import linear_sum_assignment

# Cost matrix (workers × tasks)
cost = [
    [9, 2, 7],
    [6, 4, 3],
    [5, 8, 1]
]

# Apply Hungarian Algorithm
row_ind, col_ind = linear_sum_assignment(cost)

# Display the optimal assignment
print("Optimal Assignment:")
for i in range(len(row_ind)):
    print(f"Worker {i+1} → Task {col_ind[i]+1}")

# Calculate total minimum cost
total_cost = sum(cost[i][col_ind[i]] for i in range(len(row_ind)))
print(f"\nMinimum Total Cost = {total_cost}")

📥 Input

The input is a square cost matrix (list of lists).

Worker	Task 1	Task 2	Task 3
1	9	2	7
2	6	4	3
3	5	8	1
