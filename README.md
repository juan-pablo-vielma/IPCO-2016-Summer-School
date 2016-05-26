# IPCO-2016-Summer-School

This site contains the materials for my lectures at the IPCO 2016 Summer School. Bellow you can find instructions for all the software needed for the lectures.

## Install Julia

You should use the latest version of Julia 0.4.
Binaries of Julia for all platforms are available [here](http://julialang.org/downloads/).

- Windows and Linux users should choose the 64-bit version, unless using a very old computer.

## Install IJulia/Jupyter

[Jupyter](http://jupyter.org/) is a convenient notebook-based interface to present documents which interleave code, text, and equations.
Follow the instructions [here](https://github.com/stevengj/julia-mit#installing-julia-and-ijulia) to set up IJulia.

## Install Julia packages

To start off, we will be using the following packages:
- JuMP
- GLPKMathProgInterface
- Gadfly

To install them, run the following code:
```julia
Pkg.add("JuMP")
Pkg.add("GLPKMathProgInterface")
Pkg.add("Gadfly")
```
If you have a previous installation of Julia,
be sure to update your packages to the latest version by running ``Pkg.update()``.

To test that your installation is working, run the following code (the first time you run the code you may see the message "INFO: Precompiling module JuMP" for a few minutes):

```julia
using JuMP
m = Model()
@variable(m, x >= 0)
@variable(m, y >= 0)
@constraint(m, 2x + y <= 1)
@objective(m, Max, x+y)
status = solve(m)
@show status
@show getvalue(y)
```

The output should be:

```
status = :Optimal
getvalue(y) = 1.0
```


## More resources

We will not have the time to go through all of the basic syntax points of Julia. For more materials on learning Julia,
see [here](http://julialang.org/learning/). The JuMP documentation is located [here](http://www.juliaopt.org/JuMP.jl/0.13/).
During the lecture, we will be though through some of the examples in this repository and in these
[notebooks](http://nbviewer.jupyter.org/github/JuliaOpt/juliaopt-notebooks/tree/master/notebooks/).
