Pajarito
====
#### Polyhedral Approximation in Julia: Automatic Reformulations for InTeger Optimization

Pajarito is a mixed-integer convex programming solver package that currently implements an out-of-the-box polyhedral outer approximation algorithm under src/nonlinear.jl and a finite convergence guarantee polyhedral outer approximation and branch and cut for mixed-integer conic programming algorithm under src/conic.jl.

[![Build Status](https://travis-ci.org/mlubin/Pajarito.jl.svg?branch=master)](https://travis-ci.org/mlubin/Pajarito.jl) [![codecov.io](https://codecov.io/github/mlubin/Pajarito.jl/coverage.svg?branch=master)](https://codecov.io/github/mlubin/Pajarito.jl?branch=master)

## Installation

Pajarito can be installed through git:

```
:~$ git clone https://github.com/mlubin/Pajarito.jl.git
```

under the include directory of julia. It is recommended to install [ConicNonlinearBridge.jl](https://github.com/mlubin/ConicNonlinearBridge.jl) for the conic programming subproblems in case of numerical instability. See test/ folder for examples.

## Supported solvers

Pajarito requires a mixed-integer linear programming solver and a nonlinear programming solver for src/nonlinear.jl or a conic solver for src/conic.jl. 

For MILP solver, it currently supports only [CPLEX](http://www-01.ibm.com/software/commerce/optimization/cplex-optimizer/) and [GuRoBi](http://www.gurobi.com/) for the branch and cut algorithm for mixed-integer conic programming problems. Pajarito further supports [GLPK](http://www.gnu.org/software/glpk/) for polyhedral outer approximation under both src/nonlinear.jl and src/conic.jl. MILP solver can be specified through the `mip\_solver` flag.

For NLP solver, Pajarito supports [Ipopt](https://projects.coin-or.org/Ipopt), [KNITRO](http://www.ziena.com/knitro.htm) through ConicNonlinearBridge. NLP solver can be specified through `nlp\_solver` flag.

For Conic solver, Pajarito supports [SCS](https://github.com/cvxgrp/scs), [ECOS](https://github.com/ifa-ethz/ecos), and furthermore ConicNonlinearBridge for flexible choice of a supported NLP solver (Ipopt and KNITRO). Conic solver can be specified through `conic\_solver` flag.

All solvers can have their parameters specified through their corresponding Julia interfaces.

## Supported problem classes

Pajarito supports mixed-integer smooth convex programming problems through [JuMP.jl](https://github.com/JuliaOpt/JuMP.jl) and mixed-integer disciplined convex programming problems through [Convex.jl](https://github.com/JuliaOpt/Convex.jl).

## Supported algorithms

Pajarito supports two algorithms for the mixed-integer conic programming problems. P-CB for a branch and cut algorithm and P-OA for polyhedral outer approximation algorithm. They can be specified as strings through the `algorithm` flag.

## Citing

If you find Pajarito useful in your work, we kindly request that you cite the following paper:

Lubin, Yamangil, Bent, Vielma (2016), Extended formulations in Mixed-integer Convex Programming, LNCS, IPCO 2016, Liege, Belgium (available online at http://arxiv.org/abs/1511.06710).

A preprint of this paper is freely available on [arXiv](http://arxiv.org/abs/1511.06710).

