# Python

The tutorial assumes you have already worked through the [MPI Example Tutorial](./). Therefore, the instructions here are abbreviated but will follow the same format so you may easily consult the extended tutorial.

**Table of Contents**

* [Step 1: Access Your Allocation](python.md#step-1-access-your-allocation)
* [Step 2: Create a SLURM Script](python.md#step-2-create-a-slurm-script)
  * [Example SLURM Script](python.md#example-slurm-script)
  * [SLURM Procedure](python.md#slurm-procedure)
* [Step 3: Create a Python Program](python.md#step-3-create-a-python-program)
  * [MPI Hello World Code](python.md#mpi-hello-world-code)
  * [Python Procedure](python.md#python-procedure)
* [Step 4: Run the Job](python.md#step-4-run-the-job)

📝 **Note:** Do not execute jobs on the login nodes; only use the login nodes to access your compute nodes. Processor-intensive, memory-intensive, or otherwise disruptive processes running on login nodes will be killed without warning.

## Step 1: Access Your Allocation

If you need to request an allocation, see [instructions here](../../request-access.md).

1. Open a Bash terminal \(or PuTTY for Windows users\).
2. Execute `ssh username@hpc.cofc.edu`.
3. When prompted, enter your  or  password.

## Step 2: Create a SLURM Script

### Example SLURM Script

Here is an example SLURM script for running a batch job on our HPC cluster.

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

mpirun python hello_world.py
```

1. Create your SLURM script within Vi or paste the contents of your SLURM script into Vi.
2. Save your file and return to the Bash shell.

## Step 3: Create a Python Program

### MPI Hello World Code

```python
#!/usr/bin/env python

import sys
from mpi4py import MPI

size = MPI.COMM_WORLD.Get_size()
rank = MPI.COMM_WORLD.Get_rank()
name = MPI.Get_processor_name()

print("Hello, World! I am process ",rank," of ",size," on ",name)
```

### Python Procedure

Since Python is an interpreted rather than compiled language, you do not need to compile your code.

_Python does not need to be compiled._

## Step 4: Run the Job

1. Use `sbatch` to schedule your batch job in the queue.

   ```bash
   sbatch hello_world_cpp.slurm
   ```

   This command will automatically queue your job using SLURM and produce a job ID number \(shown below\). You can check the status of your job at any time with the `squeue -j <JOB_ID>` command.

   ```bash
   squeue -j 12345
   ```

   You can also stop your job at any time with the `scancel` command.

   ```bash
   scancel 12345
   ```

2. View your results. You can view the contents of these files using the `more` command followed by the file name.

```bash
   more mpi_hello_world_py.o12345
```

Your output should look something like this \(_the output is truncated._\):

```bash
   Hello, World! I am process  11  of  20  on  compute001
   Hello, World! I am process  13  of  20  on  compute001
   Hello, World! I am process  12  of  20  on  compute001
   Hello, World! I am process  0   of  20  on  compute001
   Hello, World! I am process  15  of  20  on  compute001
   .
   .
   .
```

1. Download your results \(using the `scp` command or an SFTP client\) or move them to persistent storage.

#### Additional Examples

* [Working with C](./)
* [Working with C++](cpp.md)
* [Working with Fortran](fortran.md)
* [Working with Makefiles](makefile.md)

