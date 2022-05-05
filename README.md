# An Evaluation of Machine Learning Techniques on an Advanced Benchmark

## Wave Function Collapse

WFC is a fancy name for a relatively simple system that builds a quantum state of a puzzle and removes superpositions that violate the rules of Sudoku. It's a purely algorithmic solver (AI, not machine learning).
The system is powerful enough to solve high-difficulty solutions in less than a second. It's fully adaptable to size changes, and has the capacity to be adapted to handle advanced rules, such as the knights move, adjacency rules, and extra box shapes, with simple code addition in the propogate function. We have kept the propogation function simple, supplying only the most basic two rules - disallowing co-occurance of values in rows, columns, and boxes; and counting single-occurances of values in rows, columns, and boxes as givens (i.e. if the value 4 appears only once in row 3, we know that it has to be 4 in that spot, so we can clear the rest of the eigenstates from that position).

## Simulated Annealing

Simulated Annealing is a relative of the genetic algorithm, making modulations to a good genotype to hopefully make it better. We fill the empty spaces on teh starting board, as to satisfy the sub-grid constraints, and then switch random tiles within sub-boxes, accepting moves that get us closer to a solve. We add a temperature to this, so that more compelx moves are made (that don't necessarily lower the weight immediately), allowing us to eventually reach a solution on harer puzzles. 

## Convolutional Neural Network

CNN trained with backprop on 1 million training puzzles (-1000 test puzzles). 3 convolutional layers, each seperated by batch normalisation, followed by a dense layer, giving a probability of each of the 9 classes for each tile. We then find which probability is highest, set that, and rerun the network. We will experiment with varying sizes of training data.
