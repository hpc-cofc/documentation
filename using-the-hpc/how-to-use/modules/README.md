# Modules

Modules are a utility which allow users to load and manage applications and their versions. The modules of software packages allow you to dynamically modify your user environment by using “modulefiles.” Each modulefile contains the information needed to configure the shell for an application. After the module software package is initialized, the environment can be modified on a per-module basis using the module command, which interprets modulefiles. Typically, modulefiles instruct the module command to change or set shell environment variables such as `PATH`, `MANPATH`, and others. The modulefiles can be shared by many users on a system.

**Note:** Some modules cannot be used simultaneously, such as an Intel compiler and a GNU compiler \([information on compilers](../compilers.md)\). If you attempt to _load_ a module that is incompatible with a currently-loaded module, you will be prompted of the conflict. To avoid the error, you may have to _unload_ or _switch_ modules.


## Default Software Stack

LMOD modules are used to provision the software environment for users. The default software stack is built on GNU 8.3.0 and OpenMPI 3.1.3 MPI library.

```
user@host[~]  module list

Currently Loaded Modules:
  1) autotools   2) prun/1.2   3) gnu8/8.3.0   4) openmpi3/3.1.3   5) ohpc
```

## Switching Software Stacks

  However, you may choose to a different software stack built on a different compiler and MPI library combination. It is advisable to stick with one combination of compiler and MPI library for most of your software to avoid conflicts.

You can switch to a software stack based on GNU7 compilers and OpenMPI3 libraries or Intel compilers and OpenMPI3 libraries easily using the `module swap` option.

GNU7-OpenMPI3 Stack
```
user@host[~] module swap gnu8 gnu7

The following have been reloaded with a version change:
  1) openmpi3/3.1.3 => openmpi3/3.1.0

user@host[~]  module list

Currently Loaded Modules:
  1) autotools   2) prun/1.2   3) ohpc   4) gnu7/7.3.0   5) openmpi3/3.1.0

```

Intel-OpenMPI3 Stack
```
user@host[~]  module swap gnu8 intel

Due to MODULEPATH changes, the following have been reloaded:
  1) openmpi3/3.1.3

user@host[~]  module list

Currently Loaded Modules:
  1) autotools   2) prun/1.2   3) ohpc   4) intel/19.0.3.199   5) openmpi3/3.1.3
```

You can see a list of all available modules using the `module avail` command.

```
user@host[~]  module avail

-------------------------------------------------------------------- /opt/ohpc/pub/moduledeps/gnu8-openmpi3 --------------------------------------------------------------------
   adios/1.13.1     fftw/3.3.8      mpiP/3.4.1              netcdf/4.6.2          pnetcdf/1.11.0      py3-mpi4py/3.0.0    scorep/4.1            tau/2.28
   boost/1.69.0     hypre/2.15.1    mumps/5.1.2             opencoarrays/2.2.0    ptscotch/6.0.6      py3-scipy/1.2.1     sionlib/1.7.2         trilinos/12.12.1
   dimemas/5.3.4    imb/2018.1      netcdf-cxx/4.3.0        petsc/3.10.3          py2-mpi4py/3.0.0    scalapack/2.0.2     slepc/3.10.2
   extrae/3.5.2     mfem/3.4        netcdf-fortran/4.4.5    phdf5/1.10.4          py2-scipy/1.2.1     scalasca/2.4        superlu_dist/6.1.1

------------------------------------------------------------------------ /opt/ohpc/pub/moduledeps/gnu8 -------------------------------------------------------------------------
   hdf5/1.10.4        likwid/4.3.3    mpich/3.3       ocr/1.0.1         openmpi3/3.1.3 (L)    py2-numpy/1.15.3    superlu/5.2.1
   impi/2019.3.199    metis/5.1.0     mvapich2/2.3    openblas/0.3.5    pdtoolkit/3.25        py3-numpy/1.15.3

-------------------------------------------------------------------------- /opt/ohpc/pub/modulefiles ---------------------------------------------------------------------------
   EasyBuild/3.7.1           clustershell/1.8    gnu7/7.3.0           intel/19.0.3.199        papi/5.6.0        singularity/2.6.0
   autotools          (L)    cmake/3.12.2        gnu8/8.3.0    (L)    llvm5/5.0.1             pmix/2.1.4        valgrind/3.13.0
   charliecloud/0.9.2        cuda/9.2            hwloc/1.11.10        ohpc             (L)    prun/1.2   (L)

  Where:
   L:  Module is loaded
```



## Summary of Module Commands

| Command | Description |
| :--- | :--- |
| module list | Lists modules currently located in user's environment |
| module avail | Lists all available modules on a system in condensed format |
| module avail -l | Lists all available modules on a system in long format |
| module display | Shows environment changes that will be made by loading a given module |
| module load | Loads a module |
| module unload | Unloads a module |
| module help | Shows help for a module |
| module swap | Swaps a currently loaded module for an unloaded module |

**Modules: Local repository**  
 By default the local repository is used as a source of software installations. To list available modules, type `module avail`. To load a module, use `module load module_name`. Similarly, unload modules by typing `module unload module_name`.

## Available Modules

To see a list of available modules, type

```bash
module avail
```

📝 **Note:** If you need a module that is not available, please [contact us](../../../support.md).

You can check for the existence of a module and its versions using `module avail <module-name>`.

```bash
$ module avail cuda

----------------- /software/dev_tools/swtree/cs400/modulefiles -----------------
cuda/6.5          cuda/7.5(default)       cuda/8.0
```

## Working with Modules

When you load a module, your environment is modified to use a specific software package. To load a module:

```bash
module load vmd
```

To verify your module has loaded, you can type `module list`.

To display information about the attributes of the module such as the size of the module, the compiler or the source from which the module was created, etc., use the following command:

```bash
module display your_module
```

## Removing and Switching Modules

Unloading a module will avoid conflict and/or messages of failure due to different versions or dependencies.

```bash
module unload PE-gnu/1.0
```

Switching between different module versions can accomplish the task of having to load, unload and load modules in multiple steps. In the following example, `cuda/7.5` is currently loaded. After running the command, `cuda/7.5` is _unloaded_ and `cuda/8.0` is _loaded_.

```bash
module switch cuda/7.5 cuda/8.0
```

You can unload all the modules on your environment, by executing the module purge command:

```bash
module purge
```

<!--
## Related Information

* Environment Customization](../environment.md
-->
