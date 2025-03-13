# sorting-networks
A comparator network Cn,k: k parallel horizontal lines, called wires (channels), 
and a sequence of n vertical segments, each connecting two wires,
called comparators.
A comparator network is called a sorting network if its output is sorted
ascending for every possible input.
task: the min number of comparators needed to create a sorting
network on n wires

Sorting Networks and Minimal Comparator Problem
Introduction
Sorting networks are specialized hardware-based or parallel computing models that sort a fixed number of inputs using a predefined sequence of comparisons. The goal of this project is to determine the minimum number of comparators required to construct an optimal sorting network for n wires.

State of the Art (SOTA) Approaches
2.1 Bubble Sort Networks
Uses O(n²) comparators.
Simple but inefficient for large n.

2.2 Insertion Sort Networks
Similar to bubble sort, not optimal.

2.3 Bitonic Sort Networks (Batcher’s Method, 1968)
Uses divide-and-conquer strategy.
O(n log² n) comparators.

2.4 Odd-Even Mergesort (Batcher, 1968)
Another efficient approach.
Also achieves O(n log² n) complexity.

2.5 AKS Sorting Network (Ajtai, Komlós, Szemerédi, 1983)
First optimal network with O(n log n) comparators.
Not practical due to large constant factors.

2.6 Recent Advances
SAT solvers, brute-force search, and optimization techniques.
Genetic programming and integer programming for better networks.
Exact solutions found for small n (e.g., Knuth’s optimal networks for n ≤ 8).

Benchmark Instances
Known optimal networks for small n:
n = 4 → 5 comparators
n = 5 → 9 comparators
n = 6 → 12 comparators
n = 7 → 16 comparators
n = 8 → 19 comparators
For n > 10, exact minimal networks remain unknown.
Benchmarking strategies:
Compare runtime and complexity.
Evaluate scalability.
Use real-world datasets for experimental validation.

Conclusion & Next Steps
Summarize findings on minimal comparators.
Future work: optimization using machine learning, heuristics, and SAT solving for n > 10.
