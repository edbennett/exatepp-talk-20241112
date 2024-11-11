# Benchmarking

-

## DiRAC Technical Assessment

<div id="left">

- Work over Summer 2023 to
  - Understand current research performance characteristics
  - Identify appropriate software and resources
- There remains work to be done on optimisation of Sp(2$N$) implementation

![NVIDIA timeline](./figs/su3_timeline.png) <!-- .element height="200px" --> ![NVIDIA timeline](./figs/sp4_timeline.png) <!-- .element height="200px" --> 

![NVIDIA timeline](./figs/sp4_timeline_long.png) <!-- .element style="margin-top: -20px;" -->


</div>

<div id="right">

![Graph of multi-representation performance](./figs/grid-hirep-mr.png)
![Graph of Hasenbusch-accelerated performance](./figs/grid-hirep-hb.png)

</div>

-

## H100 benchmarks

<div id="left">

- Access via Boston Labs to two systems
  - Supermicro with 2$\times$ NVIDIA H100 PCIe
  - 1$\times$ NVIDIA DGX-H100
- Test Grid ITT benchmark, SU(3) and SU(4)
  - DGX outperforms PCIe even for one GPU for SU(3)
  - SU(4) scales slightly better than SU(3) as expected

</div>

<div id="right">

![Plot of Grid ITT benchmark comparison point on the machines tested, plus one node of CSD3 for comparison](./figs/h100.png)

</div>

-

## BSMBench and ![SOMBRERO](./images/sombrero-logo.svg) <!-- .element width="500px" style="vertical-align: -69px; margin-left: 5px;" -->

- Two mini-app benchmarks based on HiRep code
- [BSMBench](https://gitlab.com/edbennett/BSMBench)
  - Matter field square-norm, matrix-vector multiplication, <br>$D$ application
  - SU(2) adjoint, SU(3) fundamental, SU(6) fundamental
  - Constructed manually, stripping out unneeded code
- [SOMBRERO](https://github.com/sa2c/SOMBRERO)
  - CG inversion of Dirac operator
  - SU(2) fundamental, SU(2) adjoint, SU(3) fundamental, <br>SU(3) symmetric, Sp(4) fundamental, Sp(4) adjoint
  - Built automatically from HiRep using [Shoplifter](https://github.com/sa2c/shoplifter)
- Both used in UK HPC procurements


-

## BKeeper

- Grid incorporates benchmarks,
  but none equivalent to SOMBRERO
- We would like a like-for-like comparison
- We implement BKeeper,
  a Grid client application implementing the same tests as SOMBRERO
  - In principle extensible to arbitray fermion formulation
- Provides an estimate of "useful FLOP/s"
  - Compute ideal number of FLOP/s required for computation,
    divide by time
  - Allows for like-for-like comparison free of implementation details

-

## BKeeper vs SOMBRERO

![Plot of BKeeper results](./images/bkeeper-test.svg) <!-- .element width="2000px" -->

-

## Continuous benchmark

- We would like
  - Monitor our running systems
    - Ensure that performance does not degrade over time
  - Rapidly test new systems as they become available
    - Inform decisions as to what to procure
  - Check for performance regressions between software versions
- Developing tooling for this
  - Deployment based on [Reframe](https://github.com/ukri-excalibur/excalibur-tests) in preparation
  - Additional tools for scripting testing of new machines under development
