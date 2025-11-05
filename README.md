# Hungarian Algorithm & Welsh–Powell Algorithm

## 📘 Overview
This project demonstrates two classic algorithms used in **optimization** and **graph theory**:

1. **Hungarian Algorithm** → Solves the *Assignment Problem* (minimum total cost).  
2. **Welsh–Powell Algorithm** → Solves the *Graph Coloring Problem* (minimum number of colors).

Each section includes explanation, step-by-step process, **Python implementation**, and **input/output examples**.

---

# 🔢 1. Hungarian Algorithm

## 🧠 Description
The **Hungarian Algorithm** (Kuhn–Munkres Algorithm) solves the **Assignment Problem**, where the goal is to assign `n` workers to `n` tasks in a way that **minimizes total cost**.

---

## ⚙️ Steps
1. Subtract the minimum value in each row from all elements in that row.  
2. Subtract the minimum value in each column from all elements in that column.  
3. Cover all zeros using the smallest number of lines (rows or columns).  
4. If the number of lines = number of rows, the optimal solution is found.  
5. Otherwise, adjust uncovered elements and repeat the process.  
6. Finally, select one zero per row/column for the optimal assignment.

---

## 💻 Python Implementation
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

# Display optimal assignment
print("Optimal Assignment:")
for i in range(len(row_ind)):
    print(f"Worker {i+1} → Task {col_ind[i]+1}")

# Calculate minimum total cost
total_cost = sum(cost[i][col_ind[i]] for i in range(len(row_ind)))
print(f"\nMinimum Total Cost = {total_cost}")
