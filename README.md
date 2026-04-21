# CO_mindset-heuristic

Greedy heuristic for the **minimum distance-*d* dominating set** problem. Combinatorial Optimization course project (CO — *Badania Operacyjne*).

## Problem

Given an undirected graph `G = (V, E)` and an integer `d`, find a minimum-size subset `S ⊆ V` such that every vertex in `V` is within distance `d` of at least one vertex in `S`.

## Approach

1. **Precompute** — BFS from every vertex to get its *d-neighborhood* (all vertices reachable within `d` hops).
2. **Greedy pick** — repeatedly select the still-undominated vertex whose *d*-neighborhood covers the most uncovered vertices. Stop when every vertex is dominated.

Simple, fast, and gives a reasonable approximation to the NP-hard optimum. The core is in `OptimizedSolver`, with bounds-checking, timing, and a validation pass that verifies the returned set really does dominate the graph.

## Input / output

```
n m d
u_1 v_1          # m edges, 0-indexed
...
u_m v_m
```

Output: size of the dominating set followed by its member indices.

## Test cases

`test00.in` … `test07.in` with matching `.out` files — instances up to ~1000 vertices and 1500–2000 edges, with `d ∈ {1, 2, 3, 4}`.

## Build

```bash
cmake -S . -B build
cmake --build build
./build/MinimumDominatingSet_Heuristic < test01.in
```

Requires C++20.
