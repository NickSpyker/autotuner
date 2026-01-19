<h1 align="center">AutoTuner<br>Empirical Optimization for Hybrid Algorithms</h1>

<p align="center">Empirical autotuning framework that turns performance benchmarks into compile-time constants for adaptive algorithm selection.</p>

## Overview

Autotuner removes the guesswork from performance optimization by automating the creation of hybrid (adaptive) algorithms.

In high-performance computing, a single algorithm is rarely optimal for all input sizes.
For instance, matrix multiplication might benefit from a simple naïve implementation for small matrices, Strassen's algorithm for medium sizes, and a tiled parallel approach for large inputs.
Developers often hand-pick **magic numbers** (thresholds) to switch between these implementations, but these guesses are rarely perfect and vary significantly across hardware.

Autotuner solves this by:

1. Benchmarking: Running your provided implementations against varying input sizes on the target hardware.
2. Analyzing: Automatically detecting the exact **crossing points** where one algorithm outperforms another.
3. Generating: Exporting these thresholds as compile-time constants.

This allows your code to perform zero-cost dispatch at runtime, ensuring your application always uses the statistically fastest algorithm for any given workload, tailored specifically to the machine it runs on.

Key Features:

- Offline Autotuning: Heavy benchmarking happens once (or in CI), not at runtime.
- Hardware Aware: Generates configuration files specific to the CPU architecture.
- Zero-Overhead Dispatch: Uses generated const thresholds for conditional branching, avoiding dynamic lookup costs.

## License

See [LICENSE-APACHE](LICENSE-APACHE) and [LICENSE-MIT](LICENSE-MIT) for details.
