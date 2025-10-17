======================================================
KNAPSACK OPTIMIZATION: LOCAL SEARCH ASSIGNMENT
======================================================

This assignment contains Python solutions for maximizing the value of items packed into a knapsack, subject to multiple weight limits. This is known as the Multidimensional Knapsack Problem.

Since the problem is very hard, we use smart guessing methods called **heuristics** and **local search** instead of methods that guarantee the perfect answer.

------------------------------------------------------
1. THE CORE METHOD: HILL CLIMBING
------------------------------------------------------

The main algorithm is **Hill Climbing (Local Search)**. Think of it as climbing a mountain: you only take steps that move you straight up until you hit a peak.

A. FITNESS FUNCTION (Our 'Altitude')

To evaluate how good a solution is, we use a single **Fitness Score**. This score handles both the item's value and the weight limits:

    Fitness = (Total Value) - (VERY Large Penalty) * (Total Weight Violation)

* **Goal:** The search always moves to the solution with the highest possible Fitness Score.
* **Penalty:** We use a huge penalty so that any solution that breaks a weight limit (is infeasible) gets a terrible score. This forces the algorithm to find valid solutions.

B. MOVES 

The algorithm explores small changes to the current selection of items:
1.  **ADD:** Put one item in the knapsack.
2.  **DROP:** Take one item out of the knapsack.
3.  **SWAP:** Trade one item in the knapsack for one item outside.

The search stops when no single move can improve the Fitness Score 

------------------------------------------------------
2. PROBLEMS AND SCALABILITY
------------------------------------------------------

| Problem | Items (N) | Dimensions (M) | Neighborhood Size | Method Used |
|---|---|---|---|---|
| **P1 (Small)** | 20 | 2 | Small (440 moves) | **Standard Hill Climbing** |
| **P2 (Medium)** | 100 | 10 | Medium (10,000 moves) | **Standard Hill Climbing** |
| **P3 (Massive)** | 5000 | 100 | Huge (25 Million moves) | **Stochastic Local Search (SLS)** |

### WHY SLS IS NEEDED FOR PROBLEM 3

For Problem 3, checking 25 million moves in every single step of the search would take hours. To make the problem solvable in seconds, we use **Stochastic Local Search (SLS)**:

* Instead of checking every move, we **randomly sample** a small number of moves (e.g., 5,000) in each step.
* We only move to the best solution *found within that sample*.
* This is much faster but means we don't guarantee finding the absolute best possible local peak.

------------------------------------------------------
4. CONCEPTS
------------------------------------------------------
* **Feasibility:** A solution is feasible if its total weight in ALL dimensions is less than or equal to the capacity limits.
* **Local Optimum:** The best solution reachable from the starting point through single steps of improvement. Hill Climbing guarantees finding this, but not necessarily the overall best (Global Optimum).