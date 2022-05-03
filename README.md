# An Evaluation of Machine Learning Techniques on an Advanced Benchmark

## Wave Function Collapse

WFC is a fancy name for a relatively simple system that builds a quantum state of a puzzle and removes superpositions that violate the rules of Sudoku. It's a purely algorithmic solver (AI, not machine learning).
The system is powerful enough to solve high-difficulty solutions in less than a second. It's fully adaptable to size changes, and has the capacity to be adapted to handle advanced rules, such as the knights move, adjacency rules, and extra box shapes, with simple code addition in the propogate function. We have kept the propogation function simple, supplying only the most basic two rules - disallowing co-occurance of values in rows, columns, and boxes; and counting single-occurances of values in rows, columns, and boxes as givens (i.e. if the value 4 appears only once in row 3, we know that it has to be 4 in that spot, so we can clear the rest of the eigenstates from that position).

The system is functional, finding an average of 1.39 seconds per solve, with a peak at 1.64 and a trough at 1.32 seconds, and a 98.46% accuracy when tested against 10000 random 9x9 puzzles.

## Simulated Annealing

Simulated Annealing is a relative of the genetic algorithm, making modulations to a good genotype to hopefully make it better. We fill the empty spaces on teh starting board, as to satisfy the sub-grid constraints, and then switch random tiles within sub-boxes, accepting moves that get us closer to a solve. We add a temperature to this, so that more compelx moves are made (that don't necessarily lower the weight immediately), allowing us to eventually reach a solution on harer puzzles. Easy puzzle took 1.24 seconds, medium took 11.58 seconds, and hard took 183.91 seconds. This is slower than the WFC solver.

SA was able to solve a 25x25 puzzle in 18.57 minutes. WFC was not able to solve a 25x25 sudoku.

Genetic algorithms are often slow, seing as they are quite simple systems. This system found a 99.02% accuracy across the 10000 puzzles. 

## Convolutional Neural Network

CNN trained with backprop on 1 million training puzzles (-10000 test puzzles). 3 convolutional layers, each seperated by batch normalisation, followed by a dense layer, giving a probability of each of the 9 classes for each tile. We then find which probability is highest, set that, and rerun the network. It's barely slower than WFC, taking but faster than simulated annealing, giving a 99.97% accuracy across 10000 puzzle (3 incorrect). It takes 3.61 seconds on average, peaking at 4.14 seconds.

50000 for trivial, 100k for easy, 500k for medium, 1 mil for hard. accuracies of 2.56, 14.67, 68.23, and 99.97 respectively. Highest accuracy, relatively fast, averaging 2.7 seconds per solve on a trained model, with a variation of no more than 1.3 seconds.
