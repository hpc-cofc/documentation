---
description: 'See examples at https://github.com/hpc-cofc/example-runs/tree/master/06_Matlab'
---

# Matlab

## Matlab 2019a/2018b/2018a/2017b

Matlab is a general numerical simulation package that is known both for its powerful features and efficiency.

While most people use Matlab in interactive mode running on one CPU core, it does have capabilities to run on HPCs using a batch queue manager. We encourage users to do some testing on the login node and do their production runs by submitting them to compute nodes via the batch scheduler.

### What versions of Matlab are available?

You can always execute `module spider matlab` to see what versions of Matlab are available. In our case, you should see something like this:

```text
user@localhost>  module spider matlab

----------------------------------------------------------------------
  math/matlab:
----------------------------------------------------------------------
    Description:
      Application for computational chemistry and biochemistry

     Versions:
        math/matlab/r2017b
        math/matlab/r2018a
        math/matlab/r2018b
        math/matlab/r2019a

------------------------------------------------------------------------
  For detailed information about a specific "math/matlab" module (including how to load the modules) use the module's full name.
  For example:

     $ module spider math/matlab/r2019a
------------------------------------------------------------------------
```

## Operation Modes

### Interactive mode on login node

### Interactive mode on compute nodes

### Batch mode on compute nodes

### How to run

There are very good instructions on adapting Matlab to run optimally on an HPC system [here](https://github.com/UtrechtUniversity/MATLAB-on-HPC/blob/master/Part-3-Parallel-Matlab.) 

