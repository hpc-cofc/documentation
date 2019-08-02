# Software

<!--
## SoftwareStack
The cluster runs OpenHPC stack on top of a CentOS 7.6 operating system.

|     | Available component                |
|:--------:|------------------------------------|
| Base OS   | CentOS 7.6 x86_64 |
| Compilers   | GNU6(gcc, g++, gfortran), Intel |
| Math/Numerical Libraries | BLAS, LAPACK, OpenBLAS, ATLAS, MKL, Scalapack |
| MPI libraries | OpenMPI, MPICH, MPICH2, MVAPICH, IMPI |
| I/O libraries |  HDF5(pHDF), NetCDF |
| Development tools | Autotools (autoconf, automake, libtool), Valgrind |
| Debugging and profiling tools | Gprof, TAU |

Some of the underlying management components are:

|        | Available component                |
|:--------:|------------------------------------|
| Node provisioning   | Warewulf |
| Resource management | SLURM |
| Software provisioning | Modules, Built using Lmod/easybuild/Spack |
| Cluster monitoring | Ganglia, Nagios |

## Application Access
A wide range of software from specific disciplines as well as general ones (Python, R, C, C++) will be pre-compiled and provisioned as `modules` users can load at run time. If there is a particular software users want to use, please submit a request to have them installed in a central location. Otherwise, users can install them in their own area for their personal use. If users prefer working with containers, we encourage using `Singularity` containers which are preferred over `Docker` for HPC applications.

### Provisioning Software Using Modules
Our software environment uses LMod [modules](../how-to-use/modules/) to set paths to executables, libraries, include files and manual pages for the installed software. The software modules available to users are organized according to the compiler and MPI library to ensure that the environment is set up properly to run the applications.  
-->

## List of available software (as of 05/17/2019)

You can always get a list of all available modules by entering `module spider`. Here is the current list:

| Application | Versions     | Description|
|:-----------|:--------------|:-----------|
| adios |  adios/1.12.0, adios/1.13.1 |   The Adaptable IO System (ADIOS) |
| anaconda2 |  anaconda2/2019.03 |   Anaconda environment based on Python 2.7 |
| anaconda3 |  anaconda3/2019.03 |   Anaconda environment based on Python 3.7 |
| autotools |  autotools |   Developer utilities |
| boost |  boost/1.66.0, boost/1.69.0 |   Boost free peer-reviewed portable C++ source libraries |
| charliecloud |  charliecloud/0.9.2 |   Lightweight user-defined software stacks for HPC |
| chem/aimall |  chem/aimall/19_02_13 | Bader's atoms-in-molecules tools for chemistry by Todd A. Keith |
| chem/amber |  chem/amber/18-cpu, chem/amber/18-gpu |   Application for computational chemistry and biochemistry |
| chem/chimera |  chem/chimera | UCSF molecular modeling and graphics software |
| chem/gamess |  chem/gamess/2018-R2 |   Application for computational chemistry |
| chem/gaussian |  chem/gaussian/16-B.01 |   Application for computational chemistry |
| chem/jmol  | chem/jmol | Jmol molecular visualization software |
| chem/mopac |  chem/mopac/2016 |   Application for computational chemistry |
| chem/orca |  chem/orca/4.1.2 |   Application for computational chemistry |
| chem/psi4conda |  chem/psi4conda/1.3.1 |   Application for computational chemistry |
| chem/aimall |  chem/vmd/1.9.3 |   molecular modeling and graphics software |
| chem/vmd |  chem/vmd/1.9.3 |   molecular modeling and graphics software |
| clustershell |  clustershell/1.8 |   VIM files for ClusterShell |
| cm1 |  cm1/19.8-omp |   Atmospheric physics simulation package |
| cmake |  cmake/3.12.2 |   CMake is an open-source, cross-platform family of tools designed to build, test and package software. |
| cuda |  cuda/9.2, cuda/10.1 |   CUDA Compiler and Library |
| dimemas |  dimemas/5.3.4 |   Dimemas tool |
| EasyBuild |  EasyBuild/3.7.1 |   Build and installation framework |
| extrae |  extrae/3.5.2 |   Extrae tool |
| fftw |  fftw/3.3.7, fftw/3.3.8 |   A Fast Fourier Transform library |
| gdal |  gdal/2.2.3 |   A GIS format library |
| geopm |  geopm/0.6.1 |   Global Extensible Open Power Manager |
| geos |  geos/3.7.2 |   GEOS (Geometry Engine - Open Source) is a C++ port of the Topology Suite (JTS) |
| gnu |  gnu/5.4.0 |   GNU Compiler Family (C/C++/Fortran for x86_64) |
| gnu7 |  gnu7/7.3.0 |   GNU Compiler Family (C/C++/Fortran for x86_64) |
| gnu8 |  gnu8/8.3.0 |   GNU Compiler Family (C/C++/Fortran for x86_64) |
| gsl |  gsl/2.4, gsl/2.5 |   GNU Scientific Library (GSL) |
| hdf5 |  hdf5/1.10.2, hdf5/1.10.4 |   A general purpose library and file format for storing scientific data |
| hwloc |  hwloc/1.11.10 |   Portable Hardware Locality |
| hypre |  hypre/2.13.0, hypre/2.15.1 |   Scalable algorithms for solving linear systems of equations |
| imb |  imb/2018.1 |   Intel MPI Benchmarks (IMB) |
| impi |  impi/2019.3.199 |   Intel MPI Library (C/C++/Fortran for x86_64) |
| intel |  intel/19.0.3.199 |   Intel Compiler Family (C/C++/Fortran for x86_64) |
| likwid |  likwid/4.3.3 |   Toolsuite of command line applications for performance oriented programmers |
| llvm5 |  llvm5/5.0.1 |   LLVM Compiler Infrastructure |
| metis |  metis/5.1.0 |   Metis development files |
| math/matlab |  math/matlab/r2019a, math/matlab/r2018b, math/matlab/r2018a, math/matlab/r2017b | General numerical and symbolic simulation |
| mfem |  mfem/3.4 |   Lightweight, general, scalable C++ library for finite element methods |
| mkl |  mkl/19.0.3.199 |   Intel Math Kernel Library for C/C++ and Fortran |
| mpiP |  mpiP/3.4.1 |  a lightweight profiling library for MPI applications. |
| mpich |  mpich/3.2.1, mpich/3.3 |   MPICH MPI implementation |
| mumps |  mumps/5.1.2 |   A MUltifrontal Massively Parallel Sparse direct Solver |
| mvapich2 |  mvapich2/2.2, mvapich2/2.3 |   OSU MVAPICH2 MPI implementation |
| netcdf |  netcdf/4.5.0, netcdf/4.6.2 |   C Libraries for the Unidata network Common Data Form |
| netcdf-cxx |  netcdf-cxx/4.3.0 |   C++ Libraries for the Unidata network Common Data Form |
| netcdf-fortran |  netcdf-fortran/4.4.4, netcdf-fortran/4.4.5 |   Fortran Libraries for the Unidata network Common Data Form |
| numpy |  numpy/1.12.1 |   NumPy array processing for numbers, strings, records and objects |
| ocr |  ocr/1.0.1 |   Open Community Runtime (OCR) for shared memory |
| ohpc |  ohpc |  |
| openblas |  openblas/0.2.20, openblas/0.3.5 |   An optimized BLAS library based on GotoBLAS2 |
| opencoarrays |  opencoarrays/2.2.0 |   ABI to leverage the parallel programming features of the Fortran 2018 DIS |
| openmpi |  openmpi/1.10.7 |   A powerful implementation of MPI |
| openmpi3 |  openmpi3/3.1.0, openmpi3/3.1.3 |   A powerful implementation of MPI |
| papi |  papi/5.6.0 |   Performance Application Programming Interface |
| parallel |  parallel/2019 |   GNU parallel is a command-line driven utility for Linux and other Unix-like operating systems which allows the user to execute shell scripts in parallel. |
| pdtoolkit |  pdtoolkit/3.25 |   PDT is a framework for analyzing source code |
| petsc |  petsc/3.8.3, petsc/3.10.3 |   Portable Extensible Toolkit for Scientific Computation |
| phdf5 |  phdf5/1.10.1, phdf5/1.10.4 |   A general purpose library and file format for storing scientific data |
| plasma |  plasma/2.8.0 |   Parallel Linear Algebra Software for Multicore Architectures |
| pmix |  pmix/2.1.4 | |
| pnetcdf |  pnetcdf/1.11.0 |   A Parallel NetCDF library (PnetCDF) |
| proj |  proj/5.2.0 |   A geospatial coordinate transformation software |
| prun |  prun/1.2 |   job launch utility for multiple MPI families |
| ptscotch |  ptscotch/6.0.6 |   Graph, mesh and hypergraph partitioning library using MPI |
| py2-mpi4py |  py2-mpi4py/3.0.0 |   Python bindings for the Message Passing Interface (MPI) standard. |
| py2-numpy |  py2-numpy/1.15.3 |   NumPy array processing for numbers, strings, records and objects |
| py2-scipy |  py2-scipy/1.2.1 |   Scientific Tools for Python |
| py3-mpi4py |  py3-mpi4py/3.0.0 |   Python bindings for the Message Passing Interface (MPI) standard. |
| py3-numpy |  py3-numpy/1.15.3 |   NumPy array processing for numbers, strings, records and objects |
| py3-scipy |  py3-scipy/1.2.1 |   Scientific Tools for Python |
| python-intel |  python-intel/2.7.15, python-intel/3.6.8 |   Python is cross-platform interpreted language. This version is optimzed by Intel |
| R |  R/3.4.2, R/3.5.0, R/3.5.2 |   R is a language and environment for statistical computing and graphics (S-Plus like). |
| RStudio | rstudio/1.2.1555 |  GUI for running R for statistical computing and graphics. |
| scalapack |  scalapack/2.0.2 |   A subset of LAPACK routines redesigned for heterogenous computing |
| scalasca |  scalasca/2.3.1, scalasca/2.4 |   Toolset for performance analysis of large-scale parallel applications |
| scipy |  scipy/0.19.1 |   Scientific Tools for Python |
| scorep |  scorep/3.1, scorep/4.1 |   Scalable Performance Measurement Infrastructure for Parallel Codes |
| scotch |  scotch/6.0.6 |   Graph, mesh and hypergraph partitioning library |
| singularity |  singularity/2.6.0 |   Application and environment virtualization |
| sionlib |  sionlib/1.7.1, sionlib/1.7.2 |   Scalable I/O Library for Parallel Access to Task-Local Files |
| slepc |  slepc/3.10.2 |   A library for solving large scale sparse eigenvalue problems |
| superlu |  superlu/5.2.1 |   A general purpose library for the direct solution of linear equations |
| superlu_dist |  superlu_dist/4.2, superlu_dist/6.1.1 |   A general purpose library for the direct solution of linear equations |
| tau |  tau/2.27, tau/2.28 |   Tuning and Analysis Utilities Profiling Package |
| trilinos |  trilinos/12.12.1 |   A collection of libraries of numerical algorithms |
| use.own |  use.own | |
| valgrind |  valgrind/3.13.0 |   Memory debugging utilities |

Over the course of May 2019, the following applications will be available for all users.

* MATLAB
* Anaconda/Jupyter Notebooks

## Provisioning software using Lmod modules
Our cluster uses [Lmod](https://lmod.readthedocs.io), a Lua-based environmental module system, to prepare the necessary environment to run your applications. It sets up proper paths to applications, libraries and header files, and allows you to change them dynamically. Moreover, it keeps track of dependencies between different components needed to run applications and ensures you have the right environment for a successful run.

## R as an example
Suppose I want to run a statistical analysis using `R` while taking full advantage of the powerful capabilities of the massively parallel architecture of the HPC. How would I go about it? Here is one way:

#### See what modules I have loaded by default
`module list`
```bash
Currently Loaded Modules:
  1) autotools   2) prun/1.2   3) gnu8/8.3.0   4) openmpi3/3.1.3   5) ohpc
```
Given that I don't see `R` loaded by default, let me see if `R` is available on the cluster.

#### See what versions of `R` are available on the cluster
`module spider R`
```bash
---------------------------------------------------------------------
  R:
---------------------------------------------------------------------
    Description:
      A language and software environment for statistical programming

     Versions:
        R/3.4.2
        R/3.5.0
        R/3.5.2
     Other possible modules matches:
        charliecloud  chem/amber  chem/orca  clustershell  extrae  hypre  
        netcdf-fortran  ocr  opencoarrays  parallel  proj  prun  scorep  
        singularity  superlu  superlu_dist  trilinos  valgrind
```

I see there are three versions of R. Let me get some detail on `R/3.5.2`

#### Get information about `R/3.5.2` are available on the cluster
`module spider R/3.5.2`
```bash
---------------------------------------------------------------------
  R: R/3.5.2
---------------------------------------------------------------------
    Description:
      A language and software environment for statistical programming


    You will need to load all module(s) on any one of the lines below
    before the "R/3.5.2" module is available to load.

      gnu8/8.3.0
      intel/19.0.3.199
```

I see `R/3.5.2` is available with the default `gnu8/8.3.0` compiler toolchain
or the more efficient `intel/19.0.3.199` compiler toolchain. I'll pick the `gnu8/8.3.0`
since it's already loaded by default.

#### Load `R/3.5.2` from `gnu8` stack
`module load R/3.5.2`

When I check what modules are loaded, I see that `R/3.5.2` is indeed added.

`module list`

```bash

Currently Loaded Modules:
  1) autotools   2) prun/1.2   3) gnu8/8.3.0   4) openmpi3/3.1.3   5) ohpc   
  6) gdal/2.2.3   7) proj/5.2.0   8) geos/3.7.2   9) gsl/2.5  10) openblas/0.3.5  
  11) R/3.5.2
```

However, I see many other applications ( `gdal/2.2.3` , `proj/5.2.0` , `geos/3.7.2` , `gsl/2.5` , `openblas/0.3.5` ) that are loaded simultaneously without my input. Why? Because some packages in `R/3.5.2` have external dependencies such as `openblas` for doing matrix operations and `gdal` for handling GIS data. Lmod modules have information about these dependencies and they use that to set up the right environment to run `R/3.5.2`

So, what do these Lmod module files look like? You can use the `module show R/3.5.2` command to see the location and content of these module files.

`module show R/3.5.2`

```bash
---------------------------------------------------------------------
   /opt/ohpc/pub/moduledeps/gnu8/R/3.5.2:
---------------------------------------------------------------------
whatis("Name: R project for statistical computing built with the gnu8 compiler toolchain. ")
whatis("Version: 3.5.2 ")
whatis("Category: utility, developer support, user tool ")
whatis("Keywords: Statistics ")
whatis("Description: R is a language and environment for statistical computing and graphics (S-Plus like). ")
whatis("URL http://www.r-project.org/ ")
load("gdal")
load("proj")
load("geos")
load("gsl")
prepend_path("PATH","/opt/ohpc/pub/libs/gnu8/R/3.5.2/bin")
prepend_path("MANPATH","/opt/ohpc/pub/libs/gnu8/R/3.5.2/share/man")
prepend_path("LD_LIBRARY_PATH","/opt/ohpc/pub/libs/gnu8/R/3.5.2/lib64")
prepend_path("LD_LIBRARY_PATH","/opt/ohpc/pub/libs/gnu8/R/3.5.2/lib64/R/library/Rcpp/libs")
setenv("R_DIR","/opt/ohpc/pub/libs/gnu8/R/3.5.2")
setenv("R_BIN","/opt/ohpc/pub/libs/gnu8/R/3.5.2/bin")
setenv("R_LIB","/opt/ohpc/pub/libs/gnu8/R/3.5.2/lib64")
setenv("R_SHARE","/opt/ohpc/pub/libs/gnu8/R/3.5.2/share")
depends_on("openblas")
help([[
This module loads the R package for statistical computing.

Version 3.5.2


]])
```

#### Run my `R` calculations and analysis

I can run R interactively on the head node for quick tests or submit more extensive calculations to run on the compute nodes via a batch scheduler (SLURM). Either way, I would need to load `R` using the `module load R/3.5.2` command to


## R as an example (Alternative)

An alternative way to see what software is available for my current software stack to enter `module avail`

`module avail`
```bash
----------------------- /opt/ohpc/pub/moduledeps/gnu8-openmpi3 -----------------------
   adios/1.13.1     mpiP/3.4.1              pnetcdf/1.11.0      scorep/4.1
   boost/1.69.0     mumps/5.1.2             ptscotch/6.0.6      sionlib/1.7.2
   dimemas/5.3.4    netcdf-cxx/4.3.0        py2-mpi4py/3.0.0    slepc/3.10.2
   extrae/3.5.2     netcdf-fortran/4.4.5    py2-scipy/1.2.1     superlu_dist/6.1.1
   fftw/3.3.8       netcdf/4.6.2            py3-mpi4py/3.0.0    tau/2.28
   hypre/2.15.1     opencoarrays/2.2.0      py3-scipy/1.2.1     trilinos/12.12.1
   imb/2018.1       petsc/3.10.3            scalapack/2.0.2
   mfem/3.4         phdf5/1.10.4            scalasca/2.4

--------------------------- /opt/ohpc/pub/moduledeps/gnu8 ----------------------------
   R/3.5.2        impi/2019.3.199    ocr/1.0.1             py2-numpy/1.15.3
   gdal/2.2.3     likwid/4.3.3       openblas/0.3.5        py3-numpy/1.15.3
   geos/3.7.2     metis/5.1.0        openmpi3/3.1.3 (L)    superlu/5.2.1
   gsl/2.5        mpich/3.3          pdtoolkit/3.25
   hdf5/1.10.4    mvapich2/2.3       proj/5.2.0

----------------------------- /opt/ohpc/pub/modulefiles ------------------------------
   EasyBuild/3.7.1              cmake/3.12.2            papi/5.6.0
   autotools             (L)    cuda/9.2                parallel/2019
   charliecloud/0.9.2           cuda/10.1        (D)    pmix/2.1.4
   chem/amber/18-cpu            gnu/5.4.0               prun/1.2            (L)
   chem/amber/18-gpu     (D)    gnu7/7.3.0              python-intel/2.7.15
   chem/gamess/2018-R2          gnu8/8.3.0       (L)    python-intel/3.6.8  (D)
   chem/gaussian/16-B.01        hwloc/1.11.10           singularity/2.6.0
   chem/mopac/2016              intel/19.0.3.199        use.own
   chem/orca/4.1.2              llvm5/5.0.1             valgrind/3.13.0
   clustershell/1.8             ohpc             (L)

  Where:
   D:  Default Module
   L:  Module is loaded

Use "module spider" to find all possible modules.
Use "module keyword key1 key2 ..." to search for all possible modules matching any of
the "keys".
```
I see that there are is an `R/3.5.2` module in the `gnu8` stack I can load up using the `module load R/3.5.2` command.

In fact, the software available to you depends a lot on the compiler and library toolchain you pick. The `gnu8`, `gnu8-openmpi3`, `intel` and `intel-openmpi3` chains have the largest collection of applications on our cluster.

### GNU8 + OpenMPI3
The default software has the following applications. More applications will be added upon request.

```bash
------------------------------ /opt/ohpc/pub/moduledeps/gnu8-openmpi3 -------------------------------
   adios/1.13.1     mpiP/3.4.1              pnetcdf/1.11.0      scorep/4.1
   boost/1.69.0     mumps/5.1.2             ptscotch/6.0.6      sionlib/1.7.2
   dimemas/5.3.4    netcdf-cxx/4.3.0        py2-mpi4py/3.0.0    slepc/3.10.2
   extrae/3.5.2     netcdf-fortran/4.4.5    py2-scipy/1.2.1     superlu_dist/6.1.1
   fftw/3.3.8       netcdf/4.6.2            py3-mpi4py/3.0.0    tau/2.28
   hypre/2.15.1     opencoarrays/2.2.0      py3-scipy/1.2.1     trilinos/12.12.1
   imb/2018.1       petsc/3.10.3            scalapack/2.0.2
   mfem/3.4         phdf5/1.10.4            scalasca/2.4

----------------------------------- /opt/ohpc/pub/moduledeps/gnu8 -----------------------------------
   R/3.5.2            likwid/4.3.3    mvapich2/2.3      openmpi3/3.1.3   (L)    py3-numpy/1.15.3
   hdf5/1.10.4        metis/5.1.0     ocr/1.0.1         pdtoolkit/3.25          superlu/5.2.1
   impi/2019.3.199    mpich/3.3       openblas/0.3.5    py2-numpy/1.15.3

------------------------------------- /opt/ohpc/pub/modulefiles -------------------------------------
   EasyBuild/3.7.1              cmake/3.12.2            papi/5.6.0
   autotools             (L)    cuda/9.2                pmix/2.1.4
   charliecloud/0.9.2           gnu7/7.3.0              prun/1.2          (L)
   chem/gamess/2018-R2          gnu8/8.3.0       (L)    singularity/2.6.0
   chem/gaussian/16-B.01        hwloc/1.11.10           use.own
   chem/mopac/2016              intel/19.0.3.199        valgrind/3.13.0
   chem/orca/4.1.2              llvm5/5.0.1
   clustershell/1.8             ohpc             (L)
   ```

### Intel + OpenMPI3
You can switch to from the default software stack build using GNU8 to one built using Intel compilers using modules:
``module swap gnu8 intel``

The Intel 19 and OpenMPI3 software stack currently has the following packages.

```bash
------------------------------ /opt/ohpc/pub/moduledeps/intel-openmpi3 ------------------------------
   adios/1.13.1     mfem/3.4                pnetcdf/1.11.0      sionlib/1.7.2
   boost/1.69.0     mumps/5.1.2             ptscotch/6.0.6      slepc/3.10.2
   dimemas/5.3.4    netcdf-cxx/4.3.0        py2-mpi4py/3.0.0    superlu_dist/6.1.1
   extrae/3.5.2     netcdf-fortran/4.4.5    py3-mpi4py/3.0.0    tau/2.28
   geopm/0.6.1      netcdf/4.6.2            scalapack/2.0.2     trilinos/12.12.1
   hypre/2.15.1     petsc/3.10.3            scalasca/2.4
   imb/2018.1       phdf5/1.10.4            scorep/4.1

---------------------------------- /opt/ohpc/pub/moduledeps/intel -----------------------------------
   R/3.4.2            likwid/4.3.3    ocr/1.0.1             py2-numpy/1.15.3
   gdal/2.2.3         metis/5.1.0     openmpi3/3.1.3 (L)    py3-numpy/1.15.3
   hdf5/1.10.4        mpich/3.3       pdtoolkit/3.25        scotch/6.0.6
   impi/2019.3.199    mvapich2/2.3    plasma/2.8.0          superlu/5.2.1

------------------------------------- /opt/ohpc/pub/modulefiles -------------------------------------
   EasyBuild/3.7.1              chem/orca/4.1.2     hwloc/1.11.10           prun/1.2          (L)
   autotools             (L)    clustershell/1.8    intel/19.0.3.199 (L)    singularity/2.6.0
   charliecloud/0.9.2           cmake/3.12.2        llvm5/5.0.1             use.own
   chem/gamess/2018-R2          cuda/9.2            ohpc             (L)    valgrind/3.13.0
   chem/gaussian/16-B.01        gnu7/7.3.0          papi/5.6.0
   chem/mopac/2016              gnu8/8.3.0          pmix/2.1.4
```

### GNU7 + OpenMPI3
You can switch to from the default software stack build using GNU7 to one built using GNU7 using modules:
``module swap gnu8 gnu7``

The GNU7 and OpenMPI3 software stack currently has the following packages.

```bash

----------------------------------- /opt/ohpc/pub/moduledeps/gnu7 -----------------------------------
   R/3.5.0    hdf5/1.10.2    mpich/3.2.1    mvapich2/2.2    openblas/0.2.20    openmpi3/3.1.0 (L)

------------------------------------- /opt/ohpc/pub/modulefiles -------------------------------------
   EasyBuild/3.7.1              cmake/3.12.2            papi/5.6.0
   autotools             (L)    cuda/9.2                pmix/2.1.4
   charliecloud/0.9.2           gnu7/7.3.0       (L)    prun/1.2          (L)
   chem/gamess/2018-R2          gnu8/8.3.0              singularity/2.6.0
   chem/gaussian/16-B.01        hwloc/1.11.10           use.own
   chem/mopac/2016              intel/19.0.3.199        valgrind/3.13.0
   chem/orca/4.1.2              llvm5/5.0.1
   clustershell/1.8             ohpc             (L)
```

### GNU + OpenMPI
If you have slightly older software that requires GNU5 compilers and OpenMPI1, you can switch from the default software stack build using GNU8 to one built using GNU5 using modules:
``module swap gnu8 gnu``

The GNU and OpenMPI software stack currently has the following packages.

```bash
--------------------------------- /opt/ohpc/pub/moduledeps/gnu-openmpi ---------------------------------
   adios/1.12.0    mumps/5.1.2             phdf5/1.10.1       scorep/3.1          trilinos/12.12.1
   boost/1.66.0    netcdf-fortran/4.4.4    scalapack/2.0.2    sionlib/1.7.1
   fftw/3.3.7      netcdf/4.5.0            scalasca/2.3.1     superlu_dist/4.2
   hypre/2.13.0    petsc/3.8.3             scipy/0.19.1       tau/2.27

------------------------------------- /opt/ohpc/pub/moduledeps/gnu -------------------------------------
   gsl/2.4            mkl/19.0.3.199    numpy/1.12.1       openmpi/1.10.7 (L)
   impi/2019.3.199    mpich/3.2.1       ocr/1.0.1          pdtoolkit/3.25
   metis/5.1.0        mvapich2/2.2      openblas/0.2.20    superlu/5.2.1

-------------------------------------- /opt/ohpc/pub/modulefiles ---------------------------------------
   EasyBuild/3.7.1              cuda/9.2                pmix/2.1.4
   autotools             (L)    gnu/5.4.0        (L)    prun/1.2            (L)
   charliecloud/0.9.2           gnu7/7.3.0              python-intel/2.7.15
   chem/gamess/2018-R2          gnu8/8.3.0              python-intel/3.6.8  (D)
   chem/gaussian/16-B.01        hwloc/1.11.10           singularity/2.6.0
   chem/mopac/2016              intel/19.0.3.199        use.own
   chem/orca/4.1.2              llvm5/5.0.1             valgrind/3.13.0
   clustershell/1.8             ohpc             (L)
   cmake/3.12.2                 papi/5.6.0
```

### Other Applications and Utilities
The applications listed above are traditional HPC software that are stored in a central location that all storage and compute nodes can access. There are other system and utility applications stored locally on the login node as well as all compute and storage nodes.

### How about Users' Own Applications
You are welcome to install and run your own applications. Here are some useful tips
* It's best to consistently stick with one compiler and MPI library if possible.
* To ease setting up the environment to run your own applications
  * You can enter `module load use.own` to create a directory called `privatemodules` in your `$HOME` directory
  * You can copy an example module file from `/opt/ohpc/pub/examples/example.modulefile` or `/opt/ohpc/pub/examples/examplempi-dependent.modulefile` and change it to match your application

### Can Users Request Applications to be installed?
Absolutely. Please submit a TeamDynamix [service request](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085) stating the application you need and any pertinent details and we will do our best to get the application available to you quickly.

Please note that some applications are trivial to install and test while others can be cumbersome. So, we can not guarantee a quick turn-around, but we will try to give you a reasonable timeline.
