# Software

## OpenHPC Stack
The cluster runs OpenHPC stack on top of a CentOS 7.5 operating system.

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

## Application software
A wide range of software from specific disciplines as well as general ones (Python, R, C, C++) will be pre-compiled and provisioned as `modules` users can load at run time. If there is a particular software users want to use, please submit a request to have them installed in a central location. Otherwise, users can install them in their own area for their personal use. If users prefer working with containers, we encourage using `Singularity` containers which are preferred over `Docker` for HPC applications.

### Provisioning software
Our software environment uses Linux environment [modules](../how-to-use/modules/) to perform this configuration. The software modules available to users also contain preconfigured [compiler toolchains](../how-to-use/compilers.md), or programming environments which include parallel compiler wrappers and associated MPI stacks. There are also [workflow tools](../how-to-use/workflows/) that may help with your applications as well.

## Modules

The HPC software environment uses Linux environment modules to manage versions and dependencies of software packages. When you load a module, it sets the environment variables necessary for running your program.

A list of available software modules can be viewed by typing `module avail`.

A list of software modules that are currently loaded can be viewed by typing `module list`.

By default the local repository is used as a source of software installations.

Additional information on HPC modules may be found [here](../how-to-use/modules/).

<!--

## Notes on Specific Software Usage

### Singularity Containers over MPI-IB

By default, Singularity does not use the InfiniBand libraries when doing message passing with MPI. In order to make sure Singularity uses the InfiniBand libraries while using MPI, perform the following step after loading the Singularity module:

```text
source sourceme_for_mpioverib
```

Following the above step, the Singularity containers should use the InfiniBand libraries when running MPI applications.

### Visualizing Remote Data over SSH using Visit

Visit is a well-known visualization software package that is available on HPC. Visit may be configured by creating the profile of HPC Condo to visualize data from your local Visit client. In order to do so, follow the steps as shown below on your local Visit:

1. Start Visit and go to `Options` → `Host profiles`
2. Press `New Host` and populate the fields as described below
   * Host nickname: `cad`
   * Remote host name: `or-condo-login.univ.edu`
   * Host name aliases: `or-condo-login#g`
   * Path to Visit installation: `/software/dev_tools/swtree/cs400_centos7.2_pe2016-08/visit/2.10.3/centos7.2_gnu5.3.0`
   * Username: `<your__id>`
3. Check the `Tunnel data ...` checkbox
4. Click on `Apply`
5. Now in the `file` → `open` menu, click on the dropdown \(▾\) and select `cad`
6. Enter your password in the dialog box that opens
7. You should be able to see your data on the HPC file system which can be opened just as if it were local data

-->
