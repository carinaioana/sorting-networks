# Sorting-networks
A comparator network Cn,k: k parallel horizontal lines, called wires (channels), 
and a sequence of n vertical segments, each connecting two wires,
called comparators.
A comparator network is called a sorting network if its output is sorted
ascending for every possible input.
task: the min number of comparators needed to create a sorting
network on n wires

# Sorting Networks: Minimum Comparator Problem

## Problem Definition

A sorting network is a special type of comparator network that correctly sorts all possible input sequences. The components include:

- **Wires**: k parallel horizontal lines (channels) that carry values
- **Comparators**: Vertical segments connecting two wires that compare values and swap them if needed
- **Goal**: Determine the minimum number of comparators required to create a valid sorting network on n wires

## State of the Art

### Theoretical Approaches

- **AKS Network** (Ajtai, Komlós, and Szemerédi): Achieves optimal O(n log n) comparators theoretically, but has impractically large constants
- **Batcher's Odd-Even Mergesort**: Uses O(n log² n) comparators with practical implementation
- **Bitonic Sort**: Another O(n log² n) approach widely used in parallel computing applications

### Computer-Assisted Methods

- **Exhaustive Search**: Effective for small networks (typically n ≤ 10)
- **SAT Solver Approaches**: Encoding the problem as Boolean satisfiability has yielded results for moderate values of n
- **Evolutionary Algorithms**: Genetic approaches have discovered efficient network configurations

### Lower Bounds
- Information theory provides a lower bound of Ω(n log n) comparators
- Tighter bounds have been proven for specific small values of n

## Benchmark Instances

Current best-known results for networks with different numbers of wires:

| n (wires) | Minimum Comparators | Status |
|-----------|---------------------|--------|
| 4 | 5 | Optimal (proven) |
| 5 | 9 | Optimal (proven) |
| 6 | 12 | Optimal (proven) |
| 7 | 16 | Optimal (proven) |
| 8 | 19 | Optimal (proven) |
| 9 | 25 | Best known (optimality unproven) |
| 10 | 29 | Best known (optimality unproven) |
| 11 | 35 | Best known (optimality unproven) |
| 12 | 39 | Best known (optimality unproven) |
| 13 | 45 | Best known (optimality unproven) |
| 14 | 51 | Best known (optimality unproven) |
| 15 | 56 | Best known (optimality unproven) |
| 16 | 60 | Best known (optimality unproven) |

The exact optimal values for n > 8 remain open problems in computer science, making these valuable benchmark instances for evaluating new algorithmic approaches.

## Research Directions

- Developing more efficient SAT encodings for larger problem instances
- Exploring hybrid approaches combining mathematical insights with computational methods
- Investigating structural properties of minimal sorting networks
- Applying machine learning techniques to discover patterns in optimal networks

## References

1. Knuth, D.E. (1998). The Art of Computer Programming, Volume 3: Sorting and Searching.
2. Batcher, K.E. (1968). "Sorting networks and their applications."
3. Ajtai, M., Komlós, J., & Szemerédi, E. (1983). "An O(n log n) sorting network."
4. Codish, M., Cruz-Filipe, L., Frank, M., & Schneider-Kamp, P. (2016). "Twenty-five comparators

## Conclusion & Next Steps
Summarize findings on minimal comparators.
Future work: optimization using machine learning, heuristics, and SAT solving for n > 10.
