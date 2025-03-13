# Sorting-networks
A comparator network Cn,k: k parallel horizontal lines, called wires (channels), 
and a sequence of n vertical segments, each connecting two wires,
called comparators.
A comparator network is called a sorting network if its output is sorted
ascending for every possible input.
task: the min number of comparators needed to create a sorting
network on n wires

# Sorting Networks: Minimum Comparator Problem

## Overview

Sorting networks are specialized computational structures that perform sorting operations through a fixed sequence of comparisons. Unlike traditional sorting algorithms, the sequence of comparisons in a sorting network is predetermined and does not adapt based on input values. This makes sorting networks particularly valuable for hardware implementations and parallel computing applications.

This document explores the current state of research on sorting networks, focusing on the fundamental problem: **What is the minimum number of comparators C(n) needed to create a sorting network on n wires?**

## Table of Contents

- [Basic Concepts](#basic-concepts)
- [Known Optimal Values](#known-optimal-values)
- [Theoretical Bounds](#theoretical-bounds)
- [Existing Approaches](#existing-approaches)
- [Construction-Based Methods](#construction-based-methods)
- [Verification and Optimization Techniques](#verification-and-optimization-techniques)
- [Parallel Depth Optimization](#parallel-depth-optimization)
- [Benchmark Instances](#benchmark-instances)
- [Recent Advances](#recent-advances)
- [Open Problems](#open-problems)
- [Research Directions](#research-directions)

## Basic Concepts

A sorting network consists of:
- **n wires** (or channels) carrying input values
- A sequence of **comparators** connecting pairs of wires
- Each comparator ensures the smaller value goes to one wire and the larger to the other

![Sorting Network Example](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e8/Sorting-network-comparator-demonstration.svg/500px-Sorting-network-comparator-demonstration.svg.png)

A network is considered a valid **sorting network** if it correctly sorts every possible input permutation. The primary measure of efficiency is the total number of comparators used.

## Known Optimal Values

Research has established the exact minimum number of comparators C(n) for small values of n:

| n | C(n) | Year Proven | Researchers |
|---|------|-------------|------------|
| 1 | 0 | Trivial | - |
| 2 | 1 | Trivial | - |
| 3 | 3 | 1960s | - |
| 4 | 5 | 1960s | - |
| 5 | 9 | 1960s | - |
| 6 | 12 | 1960s | - |
| 7 | 16 | 1969 | Floyd & Knuth |
| 8 | 19 | 1969 | Floyd & Knuth |
| 9 | 25 | 2014 | Codish et al. |
| 10 | 29 | 2014 | Codish et al. |
| 11 | 35 | 2019 | Codish, Cruz-Filipe, Frank, Schneider-Kamp |
| 12 | 39 | 2019 | Codish, Cruz-Filipe, Frank, Schneider-Kamp |
| 13 | 45 | 2019 | Codish, Cruz-Filipe, Frank, Schneider-Kamp |
| 14 | 51 | 2019 | Codish, Cruz-Filipe, Frank, Schneider-Kamp |
| 15 | 56 | 2019 | Codish, Cruz-Filipe, Frank, Schneider-Kamp |
| 16 | 60 | 2019 | Codish, Cruz-Filipe, Frank, Schneider-Kamp |

For n > 16, only bounds are known, not exact values.

## Theoretical Bounds

For the general case, we have the following asymptotic bounds:

- **Lower bound**: C(n) ≥ n log₂(n) - O(n)
  - Derived from information-theoretic arguments (comparison-based sorting requires at least log₂(n!) comparisons)

- **Upper bound**: C(n) ≤ n log₂(n) + O(n)
  - Achieved by the AKS sorting network (Ajtai, Komlós, and Szemerédi, 1983)

The gap between these bounds shows that the optimal number of comparators for sorting networks is Θ(n log n), matching the complexity of optimal comparison-based sorting algorithms.

## Existing Approaches

### Construction-Based Methods

#### Batcher's Odd-Even Mergesort (1968)
- Uses O(n log²(n)) comparators
- Based on a divide-and-conquer strategy
- Relatively simple construction
- Practical for moderate-sized networks
- Works by recursively sorting subsequences and then merging them using a specialized merge network

#### Bitonic Sort (Batcher, 1968)
- Also uses O(n log²(n)) comparators
- Particularly suitable for parallel implementation
- Creates and merges bitonic sequences (sequences that first increase, then decrease, or vice versa)
- Regular structure makes it amenable to hardware implementation

#### AKS Network (Ajtai, Komlós, and Szemerédi, 1983)
- Achieves the asymptotically optimal O(n log n) comparators
- Highly complex construction with large constants
- Not practical for implementation due to the large hidden constants
- Based on expander graphs and the "partition and expand" paradigm

#### Insertion-based Networks
- Builds networks by repeatedly inserting new elements into already sorted sequences
- Conceptually simple but not optimal for large n
- Useful for educational purposes and understanding sorting network principles

### Verification and Optimization Techniques

#### The Zero-One Principle
- **Key theorem**: If a comparator network sorts all 2ⁿ possible binary sequences (0s and 1s), it sorts all sequences of any values
- Reduces verification space from infinite to finite (2ⁿ binary sequences)
- Fundamental property that underlies many verification and optimization approaches

#### SAT Solving
- Encoding sorting network optimization as Boolean satisfiability problems
- Used to find optimal networks for small n
- Led to breakthroughs for n = 9 to 16
- Typically involves:
  1. Encoding the network structure as boolean variables
  2. Adding constraints to ensure valid comparator placement
  3. Adding constraints to ensure sorting correctness (using the zero-one principle)
  4. Minimizing the number of comparators

#### Symmetry Breaking
- Exploiting symmetries to reduce search space
- Critical for making SAT-based approaches feasible
- Includes techniques like:
  - Restricting the first layer of comparators
  - Enforcing canonical ordering of comparators
  - Exploiting permutation symmetries

#### Genetic Algorithms and Heuristic Search
- Used to find near-optimal solutions for medium-sized n
- Can incorporate domain knowledge and structural constraints
- Typically evaluate fitness based on sorting capability and comparator count
- Often combined with local optimization techniques

### Parallel Depth Optimization

While C(n) focuses on minimizing comparators, another important metric is D(n), the minimum depth of a sorting network (where depth refers to the number of parallel steps).

- **D(n) = Ω(log n)** (Lower bound from information theory)
- **D(n) = O(log² n)** achieved by Batcher's networks
- **D(n) = O(log n)** achieved by AKS network (theoretically optimal)
- For practical networks, Parberry's networks achieve good depth with reasonable comparator count

Depth-optimal networks are particularly important for parallel computing applications where the overall execution time depends on the number of sequential steps.

## Benchmark Instances

### Classic Optimal Networks

These are the standard benchmark networks with proven optimality:
- Green's network for n = 16 (60 comparators)
- The networks for n = 9 to 15 established by Codish et al.
- Knuth's optimal network for n = 8 (19 comparators)

### Standard Test Sets

When evaluating sorting networks, researchers typically use:
- All 2ⁿ binary sequences (for small n, exploiting the zero-one principle)
- Randomly generated permutations
- Adversarial inputs (e.g., reverse-sorted sequences)
- Special-case inputs (e.g., already sorted, almost sorted)

### Comparative Benchmarks

When comparing different construction methods, the following metrics are typically used:
- Total number of comparators
- Depth of the network (parallel steps)
- Specific comparator patterns (e.g., regularity)
- Scalability across different values of n

### Canonical Reference Networks

For testing and comparison, several canonical sorting networks serve as reference points:
- **Optimal networks** for n ≤ 16
- **Batcher's odd-even networks** for larger n
- **Bitonic networks** for powers of 2

## Recent Advances

The field has seen significant progress in recent years:

- Determination of C(n) for n = 9 to 16 using advanced SAT solving techniques
- Development of improved SAT encodings that can handle larger problem instances
- Creation of practical networks with fewer comparators than Batcher's networks for specific sizes
- Refinement of theoretical bounds for specific values of n
- Improved symmetry breaking and search space reduction techniques
- Connection of sorting network problems to other combinatorial optimization problems

## Open Problems

Several important questions remain open in sorting network research:

1. Determining exact values of C(n) for n > 16
2. Finding practical networks approaching the AKS theoretical bound
3. Closing the gap between upper and lower bounds on C(n)
4. Improving techniques for verification of optimality
5. Developing efficient depth-optimal networks with near-optimal comparator counts
6. Finding tighter bounds for specific network sizes

## Research Directions

Current research focuses on:

1. Developing more efficient SAT encodings for larger n
2. Finding new construction methods with better theoretical guarantees
3. Exploring hybrid approaches that combine theoretical insights with computational optimization
4. Developing efficient implementations of sorting networks for specific hardware architectures
5. Exploring connections with other combinatorial problems
6. Applying machine learning techniques to discover new network structures
7. Investigating sorting networks for specialized sorting tasks (e.g., partial sorting)
