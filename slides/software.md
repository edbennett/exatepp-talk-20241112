# Software

-

## Lattice recap

- Typical lattice volume: $96\times48^3$
- 4 spacetime dimensions
- Gauge configuration (single state of discretised gauge field):
  $96\times48\times48\times48\times4=4.2\times10^7$ matrices
- Fermions integrated out,
  but at run-time pseudofermion fields require
  $96\times48\times48\times48\times4$ vectors for each fermion species
- _Very_ large number of matrix-vector multiplications of same matrix and vector size
  - $\Rightarrow$ Lattice usually implements this directly rather than using `dgemm`

-

## Group theory

- A lot of lattice code focuses on QCD
  - Gauge symmetry is SU(3): group element is $3\times 3$, $U^\dagger U=1$
  - Quarks transform in the fundamental of SU(3): 3-element vectors
- Interest in the UK on strong dynamics beyond the Standard Model
  - SU($N$) is a simple extension from SU(3)
  - Fermions transforming in higher representations is more complicated;
    vector length $\ne$ matrix size
  - Symplectic theories Sp(2$N$) $\subset$ SU(2$N$) have an extra constraint:
    $$U\Omega U^T = \Omega,\qquad\Omega=\left[\begin{matrix}0 & \mathbb{1}_N \\\\ -\mathbb{1}_N & 0\end{matrix}\right]$$
    Gives a block structure $U=\left[\begin{smallmatrix}A&B\\\\-B&A\end{smallmatrix}\right]$

-

## Sp(2$N$) Grid integration

- Grid is highly portable, has a wide variety of algorithms
- Desirable to use for BSM studies
- Work in 2021 in Edinburgh to implement Sp(2$N$) in Grid
- Work within ExaTEPP in 2023 to polish this code to mergeability
- Work ongoing with DiRAC RSE team to optimise this implementation

-

## The Density of States

- Typical lattice Monte Carlo computes
  $\int \mathcal{D}\phi O(\phi) \mathrm{e}^{\beta S[\phi]}$
- This fails to resolve some features,
  in particular around phase transitions
- Consider instead
  $\int dE \rho(E) \mathrm{e}^{\beta E}$
- $\rho(E)$ is the _density of states_

-

## Density of States on the Lattice:

## the LLR algorithm

![An energy axis divided into small blocks, with overlapping groups of four blocks considered as an energy interval $dE$](./images/llr-de.svg) <!-- .element width="600px" -->

- Partition the energy domain of interest
- Take overlapping energy intervals of width $dE$
- In each interval, run a constrained Monte Carlo
- At regular MC time intervals, swap states between overlapping intervals
  (with some probability)
  - $\Rightarrow$ Coupled Monte Carlo

-

## Pure gauge LLR

<div style="width: 40%; float: left;" >

- Pure gauge: can sample using heat bath algorithm
- Cheap enough to run on CPU
- Can observe e.g. finite temperature phase transition

</div>

<div style="width: 60%; float: right;" >

![Figure 2 of [arXiv:2409.19426](https://arxiv.org/abs/2409.19426)](./images/llr-swallowtail.svg) <!-- .element width="800px" -->

</div>

-

## Towards LLR with fermions

- Heat bath does not work with (dynamical) matter
- Constrained heat bath cannot be domain decomposed
  - Cannot use strong scaling to obtain results more quickly
- Beginning to port LLR constraints to Grid HMC
  - Aim to finish by end of ExaTEPP (March 2025)
- Hypothetically
  - Typical lattice: $96\times48^3$
  - Typical strong scaling: $4\times2\times2\times2$
    (8 nodes $\times$ 4 GPUs) per lattice
  - Typical energy partition: 128 $dE$ replicas
  - $\Rightarrow$ 1024 nodes/4096 GPUs
