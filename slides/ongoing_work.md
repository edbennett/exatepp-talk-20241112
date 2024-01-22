# Ongoing work

-

## Grid BSM benchmarks

- Grid includes a benchmark suite
  - Used for UK and international HPC tenders
- Focuses on:
  - Micro benchmarks (memory bandwidth, inter-node comms)
  - $D$ operator performance
  - $N=3, M=3$ and $N=4, M=4$
- Building a SOMBRERO-like Grid-based benchmark
  - More choices for $N$, $M$
  - Focus at CG inversion of $D$
  - More closely reflect performance in practice
  - Directly compare with SOMBRERO

-

## SOMRERO-like Grid-based benchmark

- Motivation: Grid significantly slower for BSM than HiRep
- Grid is a flexible, write-once-run-everywhere library
- Single benchmark will allow:
  - Comparison with CPU HiRep
  - Performance tests on GPU
- Will act as a reference for optimising Grid for BSM
  - Goal is to match or exceed HiRep CPU performance
  - Can we also make a comparison for GPU in the future?

-

## SOMBRERO and HiRep

- HiRep development has had significant activity
  - New build system
  - GPU support
- Shoplifter no longer able to build SOMBRERO
- Planning work to update Shoplifter and SOMBRERO for GPU
- Investigate using SYCLomatic on updated SOMBRERO/HiRep

-

## Continuous benchmark

- Current benchmarking efforts are ad-hoc
- Plan to systematise benchmarking
  - Of existing systems (regular benchmark runs)
  - Of new systems (regularly gain access to systems from vendors; store data for comparison)
- Will make use of [Excalibur tests](https://github.com/ukri-excalibur/excalibur-tests), [ReFrame](https://github.com/reframe-hpc/reframe)
