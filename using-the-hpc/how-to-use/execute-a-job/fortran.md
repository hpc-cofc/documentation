# Working with Fortran

The tutorial assumes you have already worked through the [MPI Example Tutorial](./). Therefore, the instructions here are abbreviated but will follow the same format so you may easily consult the extended tutorial.

**Table of Contents**

* [Step 1: Access Your Allocation](fortran.md#step-1-access-your-allocation)
* [Step 2: Create a SLURM Script](fortran.md#step-2-create-a-slurm-script)
  * [Example SLURM Script](fortran.md#example-SLURM-script)
  * [SLURM Procedure](fortran.md#pbs-procedure)
* [Step 3: Compile the Fortran Program from Source](fortran.md#step-3-compile-the-fortran-program-from-source)
  * [MPI Hello World Source Code](fortran.md#mpi-hello-world-source-code)
  * [Fortran Procedure](fortran.md#fortran-procedure)
* [Step 4: Run the Job](fortran.md#step-4-run-the-job)

**Note:** Do not execute jobs on the login nodes; only use the login nodes to access your compute nodes. Processor-intensive, memory-intensive, or otherwise disruptive processes running on login nodes will be killed without warning.

## Step 1: Access Your Allocation

If you need to request an allocation, see [instructions here](../request-access.md).

1. Open a Bash terminal \(or PuTTY for Windows users\).
2. Execute `ssh username@hpc.cofc.edu`.
3. When prompted, enter your password.

## Step 2: Create a SLURM Script

### Example SLURM Script

Here is an example PBS script for running a batch job on a HPC Condo allocation.

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
module swap openmpi3 mpich  # swap the MPI library from the default 'openmpi3' to 'mpich'.
module list                 # will list modules loaded; we'll just use this to check that the modules we selected are indeed loaded
pwd                         # prints current working directory
date                        # prints the date and time

mpirun hello_world_f
```

## Step 3: Compile the Fortran Program from Source

### MPI Hello World Source Code

```text
program helloworld
use mpi
integer ierr, numprocs, procid

call MPI_INIT(ierr)

call MPI_COMM_RANK(MPI_COMM_WORLD, procid, ierr)
call MPI_COMM_SIZE(MPI_COMM_WORLD, numprocs, ierr)

print *, "Hello world! I am process ", procid, "out of", numprocs, "!"

call MPI_FINALIZE(ierr)

stop
end
```

### Fortran Procedure

1. Compile the Fortran source into a binary executable file.

   ```bash
   mpifort -o hello_world_f hello_world.f90
   ```

2. Use `ls -al` to verify the presence of the `hello_world_f` binary in your working directory.

## Step 4: Run the Job

1. Use `sbatch` to schedule your batch job in the queue.

   ```bash
   sbatch hello_world_fortran.slurm
   ```

   This command will automatically queue your job using SLURM and produce a job ID number \(shown below\).  You can check the status of your job at any time with the `squeue -j <JOB_ID>` command.

   ```bash
   squeue -j 12345
   ```

   You can also stop your job at any time with the `scancel` command.

   ```bash
   scancel 12345
   ```
3. View your results.  
    You can view the contents of these files using the `more` command followed by the file name.  


   ```bash
   more mpi_hello_world_f.o12345
   ```

   Your output should look something like this \(_the output is truncated._\):

   ```bash
   Hello world! I am process            3 out of          20 !
   Hello world! I am process            0 out of          20 !
   Hello world! I am process            1 out of          20 !
   Hello world! I am process            7 out of          20 !
   Hello world! I am process            8 out of          20 !
   Hello world! I am process            2 out of          20 !
   Hello world! I am process            6 out of          20 !
   Hello world! I am process           11 out of          20 !
   .
   .
   .
   ```

4. Download your results \(using the `scp` command or an SFTP client\) or move them to persistent storage.

#### Additional Examples

* [Working with C](./)
* [Working with C++](cpp.md)
* [Working with Python](python.md)
* [Working with Makefiles](makefile.md)
