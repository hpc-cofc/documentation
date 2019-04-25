# Software

## OpenHPC Stack
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
<!-- contain preconfigured [compiler toolchains](../how-to-use/compilers.md), or programming environments which include parallel compiler wrappers and associated MPI stacks. There are also [workflow tools](../how-to-use/workflows/) that may help with your applications as well. -->

The HPC software environment uses Linux environment modules to manage versions and dependencies of software packages. When you load a module, it sets the environment variables necessary for running your program.

A list of available software modules can be viewed by typing `module avail`.

A list of software modules that are currently loaded can be viewed by typing `module list`.

By default the local repository is used as a source of software installations.

Additional information on HPC modules may be found [here](../how-to-use/modules/).

## List of Applications
The list of applications available depends on the compiler and MPI libraries of choice. For the default GPU8 and OpenMPI3

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
