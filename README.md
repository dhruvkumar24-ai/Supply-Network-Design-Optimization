# 🏭 Supply Network Design Optimization
### MILP · Gurobi · Python · Supply Chain · OR Course Project

![Python](https://img.shields.io/badge/Python-3.7+-3776AB?style=flat-square&logo=python&logoColor=white)
![Gurobi](https://img.shields.io/badge/Gurobi-Optimizer-red?style=flat-square)
![MILP](https://img.shields.io/badge/Model-MILP-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Optimal_Solution_Found-brightgreen?style=flat-square)
![Course](https://img.shields.io/badge/IIT_Kanpur-OR_Course_Project-red?style=flat-square)

---

## 🧩 Problem Statement

A manufacturer operates **2 factories** (Liverpool & Brighton) supplying **6 customers** through a network of **6 potential depots** across the UK. The decision-maker must:

1. **Which 4 of 6 depots to open?** (Birmingham & London are fixed; choose 2 more)
2. **Should Birmingham be capacity-expanded?** (+20,000 tons for $3,000)
3. **How to route product flows** to minimize total cost?

> *Minimize total shipping cost + depot opening cost + optional expansion cost, subject to factory capacity, depot throughput, and customer demand constraints.*

---

## 📊 Network Overview

| Layer | Nodes | Key Constraint |
|---|---|---|
| Factories | Liverpool (150K tons), Brighton (200K tons) | Max supply capacity |
| Depots | 6 potential depots | At most 4 open; throughput limits |
| Customers | C1–C6 | Demand must be fully met |

---

## ⚙️ Model Formulation

**Decision Variables:**
- `flow[s,t]` — tons shipped from source `s` to destination `t`
- `open[d]` ∈ {0,1} — whether depot `d` is opened
- `expand` ∈ {0,1} — whether Birmingham capacity is expanded

**Objective:**
```
Minimize:  Σ cost[s,t] × flow[s,t]
         + Σ opencost[d] × open[d]
         + 3000 × expand
```

**Key Constraints:**
- Factory output ≤ supply capacity
- Customer demand fully satisfied
- Flow conservation at depots
- Depot throughput ≤ capacity × open[d]
- At most 4 depots open

---

## ✅ Optimal Solution

**Open Depots:** `Birmingham · London · Exeter · Northampton`

**Expand Birmingham:** ✅ Yes (+20,000 tons capacity)

**Optimal Product Flow:**

| From | To | Flow (tons) |
|---|---|---|
| Liverpool | Exeter | 40,000 |
| Liverpool | C1 | 50,000 |
| Liverpool | C6 | 20,000 |
| Brighton | Birmingham | 70,000 |
| Brighton | London | 10,000 |
| Brighton | Northampton | 25,000 |
| Birmingham | C2, C4, C5 | 70,000 |
| London | C5 | 10,000 |
| Exeter | C3 | 40,000 |
| Northampton | C4 | 25,000 |

---

## 📁 Repository Structure

```
📦 Supply-Network-Design-Optimization/
├── Supply_Network_Design_Gurobi.ipynb   # Full MILP model + Gurobi solve + results
├── README.md
└── LICENSE
```

---

## 🚀 Getting Started

```bash
pip install gurobipy pandas
```

> Gurobi Academic License required. Available free via [Gurobi Academic Program](https://www.gurobi.com/academia/academic-program-and-licenses/).

Open and run `Supply_Network_Design_Gurobi.ipynb` — all outputs are pre-computed and visible in the notebook.

---

## 🧠 Concepts Covered

`Operations Research` · `Supply Chain Optimization` · `Mixed Integer Linear Programming` · `Facility Location` · `Network Flow` · `Sensitivity Analysis` · `Combinatorial Optimization`

---

## 📚 Reference

H. Paul Williams, *Model Building in Mathematical Programming*, 5th Edition.

---

## 👤 Author

**Dhruv Kumar Sahu**
M.Tech, Industrial & Management Engineering — IIT Kanpur
GATE 2024 AIR 33 | [LinkedIn](https://www.linkedin.com/in/dhruv-kumar-sahu-157ab9193/) · [GitHub](https://github.com/dhruvkumar24-ai)
