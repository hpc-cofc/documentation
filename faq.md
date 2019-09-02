---
description: Frequently Asked Questions
---

# F.A.Q.

## System Details

### What are the system's hardware specs?

> The new cluster is composed of
>
> * **10 standard memory compute nodes** each with 2x 20-core 2.4GHz Intel Xeon Skylake CPUs, 192GB of memory and 480GB of local storage,
> * **1 large memory compute node** with 4x 20-core 2.4GHz  Intel Xeon Skylake CPUs, 1.5TB of memory and 960GB of local storage,
> * **2 GPU-containing nodes** each with 2x 12-core 2.6GHz Intel Xeon Skylake CPUs, 1 NVIDIA Tesla V100 GPU, 192GB of RAM and 480GB local storage,
> * **1 login and visualization node** with 2x 12-core 24 2.4GHz Intel Xeon Skylake CPUs, 1 NVIDIA Quadro P4000 GPU, 192GB of RAM and 480GB local storage,
> * **512TB globally-shared long-term storage**,
> * **38TB globally-shared NVMe SSD-based fast scratch storage**,
> * **All interconnected with 100Gbps Mellanox EDR InfiniBand fabric**
>
>   You can learn more about the hardware [here](overview/hardware.md)

### What kind of software stack is running on the cluster?

> It runs an **OpenHPC** software stack composed of CentOS 7.6 with WareWulf for management and provisioning, and **SLURM** as the scheduler. It has all the necessary **general as well as subject-specific software libraries and compilers** to ensure that users' software compiles and runs optimally on the cluster. You can learn more about the software on the cluster [here]()

## Accounts

### Who is eligible to use the HPC cluster?

> All CofC faculty, staff and students are eligible to use the cluster for educational or research purposes. Students need the endorsement or sponsorship of their faculty advisor or mentor. All users have to agree to the terms outlined in the [policies page](policies.md) before getting an account on the cluster.

### How does one go about getting an account to use the HPC cluster?

> * Faculty and staff can request accounts by filling out a form electronically or emailing their request to [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Requesting%20new%20faculty/staff%20account).
> * Students are eligible for accounts upon endorsement or sponsorship by their faculty/staff mentor/advisor. Their faculty/staff mentor/advisor can send an email request to [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Requesting%20new%20student%20account) on their behalf to initiate the account creation process.
> * Instructions about applying for accounts can be found [here](using-the-hpc/request-access.md)

## Access

### How do I access the cluster?

> Most user will access the cluster via SSH. If you are on campus, the HPC cluster is accessible directly via SSH from the CofC campus wired and 'eduroam' wireless network.
>
> If you are off-campus, you would need to use CofC's VPN to access the HPC resource. If you have never used CofC's HPC resources before, you would need to submit a VPN access request even if you have used CofC's VPN to access other campus resources. Instructions on access can be found [here](using-the-hpc/access-hpc/)

### If I am not comfortable with a command-line interface \(CLI\), how can I use the cluster?

> While a CLI is essential to making full use of the cluster, we do plan to provide other ways to use the cluster though a graphical user interface \(GUI\). For example, chemists can run calculations using [WebMO](https://hpc.cofc.edu/webmo). Users running Python or R will soon be able to use Jupyter Notebooks right from their web browsers.

## Software

### What kind of applications are available on the cluster?

> The parallel software available on the cluster depends on the compiler and message passing library \(MPI\) you choose. The default GNU8 compiler and OpenMPI3 library chain provides the following applications:

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

### Can users request applications to be installed?

> Absolutely. We will add applications at users' request. Please submit a TeamDynamix [service request](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085) stating the application you need and any pertinent details and we will do our best to get the application available to you quickly.
>
> Please note that some applications are trivial to install and test while others can be cumbersome. So, we can not guarantee a quick turn-around, but we will try to give you a reasonable timeline.

### Can users install their own applications?

> Yes, users are welcome to install their own applications in their `$HOME` directories and run them. If they do, here are some useful tips
>
> * It is best to consistently stick with one compiler and MPI library if possible.
> * To ease setting up the environment to run your own applications
>   * You can enter `module load use.own` to create a directory called `privatemodules` in your `$HOME` directory
>   * You can copy an example module file from `/opt/ohpc/pub/examples/example.modulefile` or `/opt/ohpc/pub/examples/examplempi-dependent.modulefile` and change it to match your application

## Learning

### What tools are available to learn about HPC?

> [HPC Carpentry](https://hpc-carpentry.github.io/) provides a robust introduction to high-performance computing. The [Software Carpentry](https://software-carpentry.org/lessons/) project it is following has excellent lessons on the Unix shell, Python, R and Matlab.

### Will there be workshops to help users learn about HPC?

> Yes, we do plan to run workshops on campus. We also track online webinars and workshops in the area where users can expand their knowledge base.

