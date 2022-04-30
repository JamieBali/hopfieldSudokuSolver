# An Evaluation of Machine Learning Techniques on an Advanced Benchmark

## Wave Function Collapse

WFC is a fancy name for a relatively simple system that builds a quantum state of a puzzle and removes superpositions that violate the rules of Sudoku. It's a purely algorithmic solver (AI, not machine learning).
The system is powerful enough to solve high-difficulty solutions in less than a second. It's fully adaptable to size changes, and has the capacity to be adapted to handle advanced rules, such as the knights move, adjacency rules, and extra box shapes, with simple code addition in the propogate function. We have kept the propogation function simple, supplying only the most basic two rules - disallowing co-occurance of values in rows, columns, and boxes; and counting single-occurances of values in rows, columns, and boxes as givens (i.e. if the value 4 appears only once in row 3, we know that it has to be 4 in that spot, so we can clear the rest of the eigenstates from that position).

The system is functional, finding an average of 0.39 seconds per solve, with a peak at 0.64 and a trough at 0.32 seconds, and a 99.86% accuracy when tested against 1000 random 9x9 puzzles.
