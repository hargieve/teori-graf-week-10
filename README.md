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
print(f"\nMinimum Total Cost = {total_cost}")# 🧩 Welsh–Powell Algorithm

## 📘 Description
The **Welsh–Powell Algorithm** is a **graph coloring algorithm** used to color the vertices of a graph using the **minimum number of colors**, such that **no two adjacent vertices share the same color**.

This algorithm is greedy and efficient, especially for small or moderately sized graphs.

---

## 🎯 Objective
To assign colors to each vertex in a way that:
- Adjacent vertices have **different colors**
- The **total number of colors** used is **as small as possible**

---

## 🧠 Use Cases
- **Exam scheduling:** Assign time slots so no two exams with common students occur simultaneously  
- **Frequency assignment:** Assign frequencies to transmitters to avoid interference  
- **Register allocation:** Assign CPU registers to variables efficiently  

---

## ⚙️ Algorithm Steps

1. **List all vertices** and calculate their degrees (number of adjacent vertices).  
2. **Sort vertices** in **descending order** of their degree.  
3. **Assign the first color** to the first vertex in the list.  
4. For all other vertices, assign the **same color** if they are **not adjacent** to any vertex already colored with that color.  
5. Repeat steps 3–4 with a **new color** for remaining uncolored vertices.  
6. Continue until **all vertices are colored**.

---

## 💻 Python Implementation

```python
# Welsh–Powell Algorithm in Python

def welsh_powell(graph):
    # Sort vertices by descending degree
    sorted_vertices = sorted(graph, key=lambda x: len(graph[x]), reverse=True)
    
    color_map = {}
    current_color = 0

    for vertex in sorted_vertices:
        if vertex not in color_map:
            # Assign new color
            color_map[vertex] = current_color
            
            # Assign same color to non-adjacent vertices
            for other in sorted_vertices:
                if other not in color_map:
                    if all(neigh not in color_map or color_map[neigh] != current_color for neigh in graph[other]):
                        color_map[other] = current_color
            
            current_color += 1

    return color_map


# Example graph (Adjacency List)
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'C', 'D'],
    'C': ['A', 'B', 'D'],
    'D': ['B', 'C']
}

# Run the algorithm
coloring = welsh_powell(graph)
print("Vertex Coloring:", coloring)

