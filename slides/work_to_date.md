# Work to date

-

## Grid Sp(2$N$) integration

<div id="left">

- Symplectic theories are a driver of UK BSM lattice
  - Implemented in HiRep in 2017&ndash;19
- Initial implementation in Grid late 2021 by AL (UoE), but not mergeable
  - Work needed to make code robust and stylistically consistent
- JL (SU) led this effort
  - Code reviews
  - Direct modifications
  - Performance regression tests
- PR submitted July 2023
- Merged October 2023

</div>

<div id="right">

<img src="./figs/sp2n-grid-github.png" alt="Screen shot of GitHub issues and pull requests" height="600px" class="fragment">

</div>

-

## DiRAC Technical Assessment

<div id="left">

- Work over Summer 2023 to
  - Understand current research performance characteristics
  - Identify appropriate software and resources
- There remains work to be done on optimisation of Sp(2$N$) implementation

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
