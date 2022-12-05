# Quantum Computing Hardware-Software Co-Design


## Efficient Quantum Instruction Sets
https://github.com/Pitt-JonesLab/slam_decomposition

Paper in prepartion for ISCA '23

We propose a collaborative design approach to select the best ratio of drive parameters that determine the best basis gate for a particular modulator.  However, the relationship between modulator drive parameters dictated by the Hamiltonian is non-linear.  This requires considering the theoretical computing power of the gate along with the practical speed limit of that gate, given the modulator drive parameters. The practical speed limit arises from the couplers' tolerance for strong driving when one or more pumps is applied,  for which some combinations can result in higher overall speed limits than others.  Moreover, as this 2Q basis gate is typically applied multiple times in succession, interleaved by 1Q gates applied directly to the qubits, the speed of the 1Q gates can become a limiting factor for the quantum circuit.  We propose a parallel drive approach that drives the modulator and qubits simultaneously, allowing a richer capability of the 2Q basis gate and in some cases for this 1Q drive time to be absorbed entirely into the 2Q operation.  This allows increasingly short duration 2Q gates while mitigating a significant source of overhead in some quantum systems.

This repository contains a transpilation pass that implements the Speed-Limit Analysis decoMposition pass. First, we build a modular framework for decomposition circuit templates with a numerical optimizer. The circuit template uses information from Monodromy Polytopes to compute the coverage sets. We compute adjusted gate durations using SpeedLimitFunctions, which output for a gate a set of scores used in the transpilation pass to select the most time-efficient basis gate.

![image](https://user-images.githubusercontent.com/47376937/205707942-18cd6764-431f-429b-a381-2d5b11ea430b.png)

## Qubit Coupling Topology Design 
https://github.com/Pitt-JonesLab/clonk_transpilation

Paper: https://arxiv.org/pdf/2205.04387

Poster: [co-design_topology_poster22.pdf](https://github.com/Pitt-JonesLab/.github/files/10156723/mckinney_evan_quantum2022.pdf)

We propose a collaboratively designed superconducting quantum computer using a Superconducting Nonlinear Asymmetric Inductive eLement (SNAIL) modulator. The SNAIL enables high-degree couplings that allow rich and highly parallel qubit connection topologies without suffering from frequency crowding.  Building on our previously demonstrated SNAIL-based quantum state router we propose a quantum 4-ary tree and a hypercube inspired corral built from interconnected quantum modules.  We compare their advantage in data movement based on necessary SWAP gates to the traditional lattice and heavy-hex lattice used in latest commercial quantum computers. We demonstrate the co-design advantage of our SNAIL-based machine with iSWAP basis gates and rich topologies against CNOT/heavy-hex and fSIM/lattice for 16-20 qubit and extrapolated designs circa 80 qubit architectures. We compare total circuit time and total gate count to understand fidelity for systems dominated by decoherence and control imperfections, respectively.

This repository contains `ConfigurableBackendV2` used to programmatically create qubit-connectivity backends. We build a transpilation pass manager suited for fast basis gate translation, and transpile from a set of circuit benchmarks, `circuit_suite.py`, onto various backends and basis gates, `backend_suite_v3.py`. In particular, we are interested in how topology diamters and average distance scale with induced data movement operations. See `HPCA_artifact.ipynb` for demo.

![image](https://user-images.githubusercontent.com/47376937/205707602-f376e5d4-d805-4ac0-9470-bf5a919d7218.png)
