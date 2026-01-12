# HAK-y-heterogenous-architecture
Hardware

Abstraction

Konversion

-y

Essentially, this is a project whose goal is to explore the idea of a single compiler target that is then converted to be used on a variety of processor types.

Essentially, a small core reads our HAKy machine code, then decides to convert it to CPU instructions, GPU instructions, FPGA logic, etc.

The goal is to both allow for simpler development for heterogenous computing, as well as allowing for "smart" optimizations that will only work at runtime for specific system uses.

There are some forseen issues though:

-The FPGA conversion step is very difficult- after all place and route is a very difficult computing problem.

-Our instruction set will have to be optimized simultaneously for pretty much any possible architecture, I have some ideas for how to do this but I need to study our potential hard targets first

-There are a lot of pieces to the optimization problem, including the core having to know whether throughput or latency is preferred. For example, maybe part of a graphics shader works best on a CPU, while the rest works best on the GPU. Running on both would create high latency, how do we know how to decide?



Modern instruction sets are very sequential, which is not good especially for FPGA logic. I propose something closer to a "Network" of instructions, a sort of dependency graph of istructions instead. The instructions will likely be larger, but more clever optimizations are possible. There is prior research in this area, look up TRIPS processor.

First step (what I am working on now)
I will be at least doing the initial development in the context of my AMD AUP-ZU3 development board, which has limitations (due to closed source software), but is very good for its price.

I will analyze the ARM instruction set used, and the results of the GPU driver reverse engineering project for the built in GPU on this board to start getting a sense of what the hard targets are.
