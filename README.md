 Multi-Start Hill Climbing for Knapsacks (MMKP)

This code solves the **Multi-Dimensional Multiple Knapsack Problem (MMKP)** using a search algorithm called **Multi-Start Hill Climbing (MSHC)**.

 What the Code Does

The main goal is to find the **highest total value** of items that can be packed into several knapsacks while strictly obeying all capacity limits across multiple weight dimensions.

 How the Algorithm Works

The search strategy combines two parts to find the best feasible solution:

1. Local Search (`hill_climb`)

* It starts at a random solution and tries to "climb" to a **local optimum**.
* It only accepts moves (e.g., shifting one item) if the resulting solution is **FEASIBLE** (doesn't break any rules) and has a **higher value**.

2. Global Strategy (`multi_hill_climbing`)

* It runs the local search **many times** (multi-start).
* Each run begins from a different **random starting point** to explore the search space widely.
* It records the **best feasible value** found across all runs as the final answer.

Problems Solved

The script demonstrates the algorithm on three different problem scales:

| Problem | Knapsacks | Items | Dimensions |
| :---: | :---: | :---: | :---: |
| **P1** | 3 | 20 | 2 |
| **P2** | 10 | 100 | 10 |
| **P3** | 100 | 5000 | 100 |
