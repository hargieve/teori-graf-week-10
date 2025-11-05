# Hungarian Algorithm & Welsh–Powell Algorithm

## Overview
This document explains two fundamental algorithms used in **optimization** and **graph theory**:

1. **Hungarian Algorithm** — for solving the **Assignment Problem** (finding the minimum total cost).  
2. **Welsh–Powell Algorithm** — for **Graph Coloring** (minimizing the number of colors used).

Both algorithms are commonly used in operations research, scheduling, and network analysis.

---

## 1. Hungarian Algorithm

### Description
The **Hungarian Algorithm**, also called the **Kuhn–Munkres Algorithm**, is a combinatorial optimization method used to solve the **Assignment Problem** in polynomial time.

It assigns *n* workers to *n* tasks so that the **total cost is minimized**.

---

### Objective
To determine the most efficient one-to-one assignment between two equal-sized sets (e.g., workers and jobs) with the **minimum possible total cost**.

---

### Steps of the Algorithm
1. **Create a Cost Matrix**  
   Represent the cost of assigning each worker to each task in an *n × n* table.

2. **Row Reduction**  
   Subtract the smallest element in each row from all elements in that row.

3. **Column Reduction**  
   Subtract the smallest element in each column from all elements in that column.

4. **Cover All Zeros**  
   Draw the minimum number of horizontal and vertical lines to cover all zeros in the matrix.

5. **Check for Optimality**  
   - If the number of lines equals *n*, an optimal assignment exists.  
   - If not, adjust uncovered elements and repeat the process.

6. **Make the Assignment**  
   Select zeros such that each worker and task are paired exactly once.

---

### Input Example
| Worker | Task 1 | Task 2 | Task 3 |
|:------:|:-------:|:-------:|:-------:|
| 1 | 9 | 2 | 7 |
| 2 | 6 | 4 | 3 |
| 3 | 5 | 8 | 1 |

---

### Output Example
| Worker | Assigned Task | Cost |
|:------:|:--------------:|:----:|
| 1 | Task 2 | 2 |
| 2 | Task 3 | 3 |
| 3 | Task 1 | 4 |

**Minimum Total Cost = 9**

---

### Summary
| Aspect | Description |
|--------|--------------|
| Algorithm Type | Optimization |
| Problem Type | Assignment Problem |
| Input | Cost Matrix |
| Output | Optimal Worker–Task Assignment |
| Objective | Minimize Total Cost |
| Time Complexity | O(n³) |
| Applications | Job scheduling, resource allocation, transportation planning |

---

## 2. Welsh–Powell Algorithm

### Description
The **Welsh–Powell Algorithm** is a **graph coloring algorithm** that assigns colors to vertices so that **no two adjacent vertices share the same color**.

It aims to use the **minimum number of colors** possible while following the adjacency rule.

---

### Objective
To color a graph’s vertices with the fewest colors possible, ensuring that connected (adjacent) vertices have **different colors**.

---

### Steps of the Algorithm
1. **List All Vertices** and determine their **degree** (the number of vertices each one is connected to).  
2. **Sort Vertices** in **descending order** of their degree.  
3. **Assign the First Color** to the vertex with the highest degree.  
4. Assign the **same color** to other vertices that are **not adjacent** to any vertex already colored with that color.  
5. **Repeat** with a new color for remaining uncolored vertices.  
6. Continue until **all vertices** are colored.

---

### Input Example
| Vertex | Adjacent Vertices |
|:------:|:-----------------:|
| A | B, C |
| B | A, C, D |
| C | A, B, D |
| D | B, C |

---

### Output Example
| Vertex | Color |
|:------:|:------:|
| B | 1 |
| C | 2 |
| A | 3 |
| D | 3 |

**Explanation:**  
- Vertices **A** and **D** can share the same color because they are not directly connected.  
- The total number of colors used is **3**.

---

### Summary
| Aspect | Description |
|--------|--------------|
| Algorithm Type | Greedy Graph Coloring |
| Problem Type | Vertex Coloring |
| Input | Graph (Adjacency List or Matrix) |
| Output | Vertex–Color Mapping |
| Objective | Minimize Number of Colors |
| Time Complexity | O(V²) |
| Applications | Exam scheduling, map coloring, frequency assignment |

---

## 3. Comparison Table

| Feature | Hungarian Algorithm | Welsh–Powell Algorithm |
|----------|----------------------|------------------------|
| Type | Optimization | Graph Coloring |
| Goal | Minimize total cost | Minimize number of colors |
| Input | Cost Matrix | Graph (Adjacency List) |
| Output | Optimal Assignment | Vertex–Color Mapping |
| Approach | Matrix-based | Degree-based Greedy |
| Time Complexity | O(n³) | O(V²) |
| Applications | Job assignment, scheduling | Map coloring, resource allocation |

---

## Conclusion
- The **Hungarian Algorithm** efficiently solves **assignment problems**, ensuring minimal cost or maximum efficiency.  
- The **Welsh–Powell Algorithm** solves **graph coloring problems**, reducing conflicts and optimizing scheduling.  

---

