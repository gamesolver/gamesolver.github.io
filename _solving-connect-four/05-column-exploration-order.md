---
title:  "Part 5 -- Column exploration order"
date:   2017-02-25 00:00:00 +0000
excerpt: "Alpha-beta is more efficient when you explore best move first"
---

Alpha-beta allows to prune the exploration tree by taking into account the score of the first explored nodes to narrow the \[alpha;beta\] exploration window of their next sibling nodes. Exploring the best node first will thus allow to have the maximal reduction of the exploration window for the next nodes. On the contrary, exploring the nodes in the worst order (start with worst score first and finish with best score) won't allow much pruning and have performance close to min-max algorithm.

There are many heuristics to try to order the possible moves in an optimal order. If you use a score function, you can use it for the next move or at a shallow depth. Other heuristics keep track of the moves that made cut-off at similar depth for previously explored nodes and try them first.

We will just implement a static column order strategy, exploring center columns first and edge columns at the end. Center columns are in average better moves in Connect 4 because they are involved in more possible alignments.


# Implementation.

Implementation is straitforward, you just need to explore the next possible moves in a different static order. The order is initialize in the constructor of the Solver class.

Here are:

- the simple [code diff](https://github.com/PascalPons/connect4/commit/6caf32a4845bf1478b0d30bebd6366bfea75b7b5
) from last alpha-beta version,
- the full [source code](https://github.com/PascalPons/connect4/releases/tag/part5) corresponding to this part.

# Benchmark

You can see that this very simple column exploration re-ordering allows to reduce significantly (more than 10-fold) the number of explored nodes and computation time. The improvement is greater for position needing deeper exploration.

|Solver                                      |Test Set name   |mean time    |mean nb pos  |K pos/s |
---------------------------------------------|----------------|-------------|-------------|--------|
|Column exploration order (strong solver)    |End-Easy        |40.86 μs     |139.7        |3,417   |
|Column exploration order (strong solver)    |Middle-Easy     |189.1 ms     |2,081,790    |11,009  |
|Column exploration order (strong solver)    |Middle-Medium   |3.48 s       |40,396,700   |11,594  |
|Column exploration order (strong solver)    |Begin-Easy      |N/A          |N/A          |N/A     |
|Column exploration order (strong solver)    |Begin-Medium    |N/A          |N/A          |N/A     |
|Column exploration order (strong solver)    |Begin-Hard      |N/A          |N/A          |N/A     |
|--------------------------------------------|----------------|-------------|-------------|--------|
|Column exploration order (weak solver)      |End-Easy        |31.16 μs     |107.1        |3,438   |
|Column exploration order (weak solver)      |Middle-Easy     |77.13 ms     |927,943      |12,031  |
|Column exploration order (weak solver)      |Middle-Medium   |1.949 s      |23,685,400   |12,153  |
|Column exploration order (weak solver)      |Begin-Easy      |N/A          |N/A          |N/A     |
|Column exploration order (weak solver)      |Begin-Medium    |N/A          |N/A          |N/A     |
|Column exploration order (weak solver)      |Begin-Hard      |N/A          |N/A          |N/A     |

*mean time*: average computation time (per test case). *mean nb pos*: average number of explored nodes (per test case).
*N/A* means that the algorithm was too slow to evaluate the 1,000 test cases within 24h.

# Tutorial plan
{% include nav_list nav="side" %}
