# Working with Makefiles

The tutorial assumes you have already worked through the [MPI Example Tutorial](./). Therefore, the instructions here are abbreviated but will follow the same format so you may easily consult the extended tutorial.

On this page, we will use a Makefile to automate the compiling of the C, C++, and Fortran programs. In our SLURM script, we will send a command to the Makefile which will compile codes prior to submitting the job to MPI.

**Table of Contents**

* [Step 1: Access Your Allocation](makefile.md#step-1-access-your-allocation)
* [Step 2: Create a SLURM Script](makefile.md#step-2-create-a-pbs-script)
  * [Example SLURM Script](makefile.md#example-slurm-script)
  * [SLURM Procedure](makefile.md#slurm-procedure)
* [Step 3: Create the Makefile](makefile.md#step-3-create-the-makefile)
  * [Makefile Code](makefile.md#makefile-code)
  * [Makefile Procedure](makefile.md#makefile-procedure)
* [Step 4: Run the Job](makefile.md#step-4-run-the-job)

**Note:** Do not execute jobs on the login nodes; only use the login nodes to access your compute nodes. Processor-intensive, memory-intensive, or otherwise disruptive processes running on login nodes will be killed without warning.

## Step 1: Access Your Allocation

If you need to request an allocation, see [instructions here](../request-access.md).

1. Open a Bash terminal \(or PuTTY for Windows users\).
2. Execute `ssh username@hpc.cofc.edu`.
3. When prompted, enter your password.

## Step 2: Create a SLURM Script

### Example SLURM Script

Here is an example SLURM script for running a batch job on our HPC.

```bash
#!/bin/bash

#SBATCH -p stdmemq          # Submit to 'stdmemq' Partitiion or queue
#SBATCH -J MPItest          # Name the job as 'MPItest'
#SBATCH -o MPItest-%j.out   # Write the standard output to file named 'jMPItest-<job_number>.out'
#SBATCH -e MPItest-%j.err   # Write the standard error to file named 'jMPItest-<job_number>.err'
#SBATCH -t 0-12:00:00        # Run for a maximum time of 0 days, 12 hours, 00 mins, 00 secs
#SBATCH --nodes=1            # Request N nodes
#SBATCH --ntasks-per-node=20 # Request n cores or task per node
#SBATCH --mem-per-cpu=4000   # Request 4000MB (4GB) RAM per core
#SBATCH --mail-type=ALL      # Send email notification at the start and end of the job
#SBATCH --mail-user=<user>@cofc.edu  # Send email notification to this address

module list                 # will list modules loaded by default. In our case, it will be GNU8 compilers and OpenMPI3 MPI libraries
pwd                         # prints current working directory
date                        # prints the date and time

make all

echo "=================================="
echo "Output of the MPI and C program"
echo "=================================="

mpirun hello_world_c

echo "=================================="
echo "Output of the MPI and C++ program"
echo "==================================="

mpirun hello_world_cpp

echo "====================================="
echo "Output of the MPI and Fortran program"
echo "====================================="

mpirun hello_world_f

echo "====================================="
echo "Output of the MPI and Python program"
echo "====================================="

mpirun python hello_world.py

echo "============================="
echo "Successful!!!... End of File"
echo "============================="
```

## Step 3: Create the Makefile

A makefile contains instructions for Make software to automate the build of programs and source codes.

### Makefile Code

This file must be located in the same path as the other source programs.

```text
CC = mpicc
CXX = mpic++
FC = mpifort

OPTFLAGS = -O3
CFLAGS = $(OPTFLAGS) -g
CXXFLAGS = $(OPTFLAGS) -g
FFLAGS = $(OPTFLAGS) -g

all:hello_world_c hello_world_cpp hello_world_f

hello_world_c: hello_world.c
        $(CC) $(CFLAGS) -o hello_world_c hello_world.c

hello_world_cpp: hello_world.cpp
        $(CXX) $(CXXFLAGS) -o hello_world_cpp hello_world.cpp

hello_world_f: hello_world.f90
        $(FC)  $(FFLAGS) -o hello_world_f hello_world.f90

clean:
        rm hello_world_*
```

**Note:** Indentations in a Makefile must be a `Tab` and not `spaces`.

## Step 4: Run the Job

1. Use `sbatch` to schedule your batch job in the queue.

   ```bash
   sbatch hello_world_make.slurm
   ```

   This command will automatically queue your job using SLURM and produce a job ID number \(shown below\). You can check the status of your job at any time with the `squeue -j <JOB_ID>` command.

   ```bash
   squeue -j 12345
   ```

   You can also stop your job at any time with the `scancel` command.

   ```bash
   scancel 12345
   ```

2. View your results.  

    You can view the contents of these files using the `more` command followed by the file name.  

```bash
   more mpi_hello_world_make.o143295
```

Your output should look something like this \(_the output is truncated._\):

```bash
   Processor compute001 ID=9  Hello world
   Processor compute001 ID=4  Hello world
   Processor compute001 ID=0  Hello world
   Processor compute001 ID=1  Hello world
   Processor compute001 ID=3  Hello world
   Processor compute001 ID=5  Hello world
   .
   .
   .
```

1. Download your results \(using the `scp` command or an SFTP client\) or move them to persistent storage.

#### Additional Examples

* [Working with C](./)
* [Working with C++](cpp.md)
* [Working with Fortran](fortran.md)
* [Working with Python](python.md)

