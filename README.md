# sorting-networks
A comparator network Cn,k: k parallel horizontal lines, called wires (channels), 
and a sequence of n vertical segments, each connecting two wires,
called comparators.
A comparator network is called a sorting network if its output is sorted
ascending for every possible input.
task: the min number of comparators needed to create a sorting
network on n wires

Sorting Networks: Minimum Comparator Problem
A sorting network is a fascinating mathematical construct that uses a fixed arrangement of comparators to sort any input sequence. Let me break down the key aspects of this problem and the state-of-the-art approaches.
Problem Definition

Sorting Network: A comparator network consisting of n wires (channels) and a sequence of comparators
Comparator: A vertical segment connecting two wires that compares and potentially swaps values
Goal: Find the minimum number of comparators needed to create a sorting network on n wires

State-of-the-Art Approaches
1. Theoretical Constructions

AKS Network (Ajtai, Komlós, and Szemerédi): Achieves O(n log n) comparators with a small constant, but impractical due to large constants
Batcher's Odd-Even Mergesort: Uses O(n log² n) comparators but is much more practical
Bitonic Sort: Another O(n log² n) approach widely used in parallel computing

2. Computer-Assisted Proofs

Exhaustive Search: For small n (typically n ≤ 10), computer searches have found optimal networks
SAT Solver Approaches: Encoding the problem as a Boolean satisfiability problem has yielded results for moderate values of n
Evolutionary Algorithms: Genetic algorithms have been applied to search for minimal networks

3. Lower Bounds

Information-Theoretic Bound: Ω(n log n) comparators are necessary
Specific Bounds: Tighter lower bounds have been proven for specific small values of n

Benchmark Instances
The most well-studied benchmark instances are networks with n = 4 through n = 16 wires. Current best-known results:
n (wires)Minimum ComparatorsStatus45Optimal (proven)59Optimal (proven)612Optimal (proven)716Optimal (proven)819Optimal (proven)925Best known (optimality unproven)1029Best known (optimality unproven)1135Best known (optimality unproven)1239Best known (optimality unproven)1345Best known (optimality unproven)1451Best known (optimality unproven)1556Best known (optimality unproven)1660Best known (optimality unproven)
The exact optimal values for n > 8 remain open problems in computer science, making these valuable benchmark instances for new algorithmic approaches.
