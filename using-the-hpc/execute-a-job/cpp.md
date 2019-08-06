# Working with C++

The tutorial assumes you have already worked through the [MPI Example Tutorial](./). Therefore, the instructions here are abbreviated but will follow the same format so you may easily consult the extended tutorial.

**Table of Contents**

* [Step 1: Access Your Allocation](cpp.md#step-1-access-your-allocation)
* [Step 2: Create a SLURM Script](cpp.md#step-2-create-a-slurm-script)
  * [Example SLURM Script](cpp.md#example-slurm-script)
  * [SLURM Procedure](cpp.md#slurm-procedure)
* [Step 3: Compile the C++ Program from Source](cpp.md#step-3-compile-the-c-program-from-source)
  * [MPI Hello World Source Code](cpp.md#mpi-hello-world-source-code)
  * [C++ Procedure](cpp.md#c-procedure)
* [Step 4: Run the Job](cpp.md#step-4-run-the-job)

**Note:** Do not execute jobs on the login nodes; only use the login nodes to access your compute nodes. Processor-intensive, memory-intensive, or otherwise disruptive processes running on login nodes will be killed without warning.

## Step 1: Access Your Allocation

If you need to request an allocation, see [instructions here](../request-access.md).

1. Open a Bash terminal \(or PuTTY for Windows users\).
2. Execute `ssh username@hpc.cofc.edu`.
3. When prompted, enter your  or  password.

## Step 2: Create a SLURM Script

### Example SLURM Script

Here is an example PBS script for running a batch job on a HPC Condo allocation.

```bash
#!/bin/bash

#SBATCH -p stdmemq           # Submit to 'stdmemq' Partitiion or queue
#SBATCH -J MPItest           # Name the job as 'MPItest'
#SBATCH -o MPItest-%j.out    # Write the standard output to file named 'jMPItest-<job_number>.out'
#SBATCH -e MPItest-%j.err    # Write the standard error to file named 'jMPItest-<job_number>.err'
#SBATCH -t 0-12:00:00        # Run for a maximum time of 0 days, 12 hours, 00 mins, 00 secs
#SBATCH --nodes=1            # Request N nodes
#SBATCH --ntasks-per-node=20 # Request n cores or task per node
#SBATCH --mem-per-cpu=4000   # Request 4000MB (4GB) RAM per core
#SBATCH --mail-type=ALL      # Send email notification at the start and end of the job
#SBATCH --mail-user=<user>@cofc.edu  # Send email notification to this address

module list                 # will list modules loaded by default.
pwd                         # prints current working directory
date                        # prints the date and time

mpirun hello_world_cpp        # run the MPI job
```

## Step 3: Compile the C++ Program from Source

### MPI Hello World Source Code

```cpp
#include<iostream>
#include "mpi.h"

using namespace std;
#include "mpi.h"

int main(int argc, char *argv[])
{
    int id, p, name_len;
    char processor_name[MPI_MAX_PROCESSOR_NAME];     
    MPI::Init(argc, argv);
    p = MPI::COMM_WORLD.Get_size();
    id = MPI::COMM_WORLD.Get_rank();
    MPI_Get_processor_name(processor_name, &name_len);
    cout<<" Processor " << processor_name<<" ID="<<id<< " Hello world\n";
    MPI::Finalize();
return 0;
}
```

### C++ Procedure

1. Compile the C++ source into a binary executable file.

   ```bash
   mpic++ -o hello_world_cpp hello_world.cpp
   ```

2. Use `ls -al` to verify the presence of the `hello_world_cpp` binary in your working directory.

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
   more mpi_hello_world_cpp.o12345
```

Your output should look something like this \(_the output is truncated._\):

```bash
   Processor compute001 ID=5 Hello world
   Processor compute001 ID=1 Hello world
   Processor compute001 ID=4 Hello world
   Processor compute001 ID=8 Hello world
   .
   .
   .
```

1. Download your results \(using the `scp` command or an SFTP client\) or move them to persistent storage.

#### Additional Examples

* [Working with C](./)
* [Working with Fortran](fortran.md)
* [Working with Python](python.md)
* [Working with Makefiles](makefile.md)

