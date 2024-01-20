# Background

-

## What's a lattice?

By analogy with crystallography: A regular array of points

![A diagram showing a three-dimensional array of white circles](figs/lattice-white.svg)

-

## Lattice Gauge Theory

The set of techniques for studying gauge theories discretised on a lattice.

- Developed in the 1970s
  - Developed from techniques in computational condensed matter physics
- The only first-principles, non-perbative method for non-Abelian gauge theories

-

## Lattice Gauge Theory

<div id="left">

- Gauge fields: $N \times N$ matrices, one per link
  - 4 per lattice site (in 4D)
- Matter fields: 4 $M$-element vectors, per site
- Derivatives in continuum Lagrangian become nearest-neighbour interactions
  - Action is local
  - Lattice can be partitioned in space, and partitions worked on independently
- Observables are path integrals
  - Use Monte Carlo integration
- Action is (usually) real
  - Use importance sampling
  - Generate configurations of the gauge field representative of distribution dictated by the action
- Characterise interaction between gauge field and matter by Dirac operator $D$
  - Nearest-neighbour interaction
  - Inversion of $D$ is >90% of execution time
</div>

<div id="right">

![A diagram showing a three-dimensional array of white circles. Some of the circles are labeled "sites". Some immediately adjacent circles have lines between them which are labeled "links". Some groups of four immediately adjacent circles have lines forming a closed loop between them, which are labeled "plaquettes".](figs/lattice-labeled.svg)

</div>

-

## Lattice practicalities

- Typical volumes: $24\times12^3$ is small, $256\times128^3$ is largest
- Physical lattice spacing is emergent, not directly set
- Boundary conditions are chosen to suit observable, but typically periodic
- $>O(10^6)$ matrices & vectors of same dimensionality
  - $\Rightarrow$ General-purpose linear algebra libraries typically not a good fit

-

## Lattice software landscape

<div class="col fragment">

![Grid logo](./images/grid.svg) <!-- .element width="150px" style="margin-top: -15px; margin-bottom: -15px;" -->

- Developed since 2015
- C++17, with expression templates
- Aims for performance portability
- Arbitrary vector length
- MPI, OpenMP
- CPU, CUDA, HIP, SYCL
- Primary focus on $N=3,M=3$
  - Flexible design

</div><div class="col fragment">

HiRep

- Developed since 2007
- C, with C++/Perl code generator
- Minimal platform-specific code
- MPI, little OpenMP
- CPU (+ CUDA under development)
- Explicit focus on general $N$, $M$

</div><div class="col fragment">

openQCD

- Developed since 2012
- C
- Some third-party platform specialisations (QPX, AVX2, AVX512)
- MPI, OpenMP
- CPU (+ CUDA under development)
- $N=3, M=3$ only

</div>

-

## BSMBench and ![SOMBRERO](./images/sombrero-logo.svg) <!-- .element width="500px" style="vertical-align: -69px; margin-left: 5px;" -->

- Two mini-app benchmarks based on HiRep code
- [BSMBench](https://gitlab.com/edbennett/BSMBench)
  - Matter field square-norm, matrix-vector multiplication, <br>Dirac operator application
  - SU(2) adjoint, SU(3) fundamental, SU(6) fundamental
  - Constructed manually, stripping out unneeded code
- [SOMBRERO](https://github.com/sa2c/SOMBRERO)
  - CG inversion of Dirac operator
  - SU(2) fundamental, SU(2) adjoint, SU(3) fundamental, <br>SU(3) symmetric, Sp(4) fundamental, Sp(4) adjoint
  - Built automatically from HiRep using [Shoplifter](https://github.com/sa2c/shoplifter)
- Both used in UK HPC procurements
