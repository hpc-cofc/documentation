# Execute a Job

The tutorial below shows you how to run Wes Kendall's basic "hello world" program, written in C, using the message passing interface \(MPI\) to scale across our HPC compute nodes [\[1\]](./#works-cited). The test will be submitted to the HPC via a [SLURM (Simple Linux Utility for Resource Management)](https://slurm.schedmd.com) batch scheduling system.

Additional examples can be found in [C++](cpp.md), [Fortran](fortran.md) or [Python](python.md) sections.

**Table of Contents**

* [Step 1: Access Your Allocation](./#step-1-access-your-allocation)
* [Step 2: Create a SLURM Script](./#step-2-create-a-SLURM-script)
  * [Example SLURM Script](./#example-slurm-script)
  * [SLURM Script Breakdown](./#slurm-script-breakdown)
  * [SLURM Procedure](./#pbs-procedure)
* [Step 3: Compile the C Program from Source](./#step-3-compile-the-c-program-from-source)
  * [MPI Hello World Source Code](./#mpi-hello-world-source-code)
  * [C Procedure](./#c-procedure)
* [Step 4: Run the Job](./#step-4-run-the-job)

**Note:** Do not execute jobs on the login nodes; only use the login nodes to access your compute nodes. Processor-intensive, memory-intensive, or otherwise disruptive processes running on login nodes will be killed without warning.

## Step 1: Access Your Allocation

1. Open a Bash terminal.
2. Execute `ssh username@hpc.cofc.edu`.
3. When prompted, enter your password.

Once you have connected to the login node, you can proceed to Step 2 and begin assembling your SLURM submission script.

## Step 2: Create a SLURM Script

Below is the SLURM script we are using to run an MPI "hello world" program as a batch job. SLURM scripts use variables to specify things like the number of nodes and cores used to execute your job, estimated walltime for your job, and which compute resources to use \(e.g., GPU _vs._ CPU\). The sections below feature an example Slurm script for our HPC resources, show you how to create and save and submit your own SLURM script to run on our HPC.

Consult the official SLURM [documentation](https://slurm.schedmd.com/documentation.html) and [FAQ](https://slurm.schedmd.com/faq.html) for a complete list of options and common questions.

### Example SLURM Script

Here is an example SLURM script for running a batch job on our HPC. Please save it to a file named `mpi-test.slurm`. We break down each command in the section below.

```bash
#SBATCH -p stdmemq          # Submit to 'stdmemq' Partitiion or queue
#SBATCH -J MPItest          # Name the job as 'MPItest'
#SBATCH -o MPItest-%j.out   # Write the standard output to file named 'jMPItest-<job_number>.out'
#SBATCH -e MPItest-%j.err   # Write the standard error to file named 'jMPItest-<job_number>.err'
#SBATCH --mail-user=<user>@cofc.edu  # Email the user on the status of the job based on the --mail-type option
#SBATCH --mail-type=ALL     # Email at the start and of the job
#SBATCH -t 0-12:00:00       # Run for a maximum time of 0 days, 12 hours, 00 mins, 00 secs
#SBATCH -N 2                # Request 2 nodes
#SBATCH -n 40               # Request 40 cores or task per node
#SBATCH --mem=180G          # Use as much as 180GB memory per node

module list                 # will list modules loaded by default. In our case, it will be GNU8 compilers and OpenMPI3 MPI libraries
module swap openmpi3/3.1.3 mpich/3.3  # swap the MPI library from the default 'openmpi3/3.1.3' to 'mpich/3.3'.
module list                 # will list modules loaded; we'll just use this to check that the modules we selected are indeed loaded
pwd                         # prints current working directory
date                        # prints the date and time

mpirun hello_world_c        # run the MPI job
```

### SLURM Script Breakdown

You can always type `man sbatch` to see all the SLURM batch submission options. Below is an explanation of the options used above.

  -  | Option   | Description
-------- |  ---------------------  | -----------------------------------------------------------------
SBATCH | -p, --partition=<partition\> | Submit the job to <partition> queue
SBATCH | -J, --job-name=<jobname\> | Name the job as <jobname>
SBATCH | -o, --output=<filename\>	| Write the job's standard output to the file name named <filename\>
SBATCH | -e, --error=<filename\>	| Write the job's standard error messages to the file name named <filename\>
SBATCH | --mail-user=<e-mail address\> | Notify user by email when certain event types occur, as specified by the --mail-type=<type\> option.
SBATCH | --mail-type=<type\> | Notify user by email when certain event types occur. <type\>=ALL notifies upon the start, end or failing of the job. <type\>=END only notified the user at the end.  
SBATCH | -N, --nodes=<n\> | Request that `n` nodes be allocated to this job.
SBATCH | -n, --ntasks-per-node=<ntasks\>  | Request that ntasks be invoked on each node.
SBATCH | --mem=<size[units]\>  | Specify the real memory required per node in the proper unit.
SBATCH | -t, --time=<time\>  | Maximum run time for your job in the format `D-HH:MM:SS`


## Step 3: Compile the C Program from Source

Below is Wes Kendall's simple "hello world" C program that utilizes MPI to run the job in parallel [\[1\]](./#works-cited). We will need to compile this source code on one of the compute nodes.

### MPI Hello World Source Code

```c
#include <mpi.h>
#include <stdio.h>

int main(int argc, char** argv) {
    // Initialize the MPI environment.
    MPI_Init(NULL, NULL);
    // Get the number of processes.
    int world_size;
    MPI_Comm_size(MPI_COMM_WORLD, &world_size);
    // Get the rank of the process.
    int world_rank;
    MPI_Comm_rank(MPI_COMM_WORLD, &world_rank);
    // Get the name of the processor.
    char processor_name[MPI_MAX_PROCESSOR_NAME];
    int name_len;
    MPI_Get_processor_name(processor_name, &name_len);
    // Print off a hello world message.
    printf("Hello world from processor %s, rank %d"
           " out of %d processors\n",
           processor_name, world_rank, world_size);
    // Finalize the MPI environment.
    MPI_Finalize();
}
```

### C Procedure

When creating and editing your `hello_world.c` source code, we will be working on the login node using the text editor such as Vi, Emacs or Nano.

1. Create a file named `hello_world.c` and paste the contents of the above code there.
2. Load the compiler and MPI library. Please note that `GNU8` and `OpenMPI3` are the defaults on our cluster. This exercise suggests that we use a different flavor of MPI called [MPICH](https://www.mpich.org/). Enter `module list` to see if what modules are loaded. If MPICH is not loaded, swap the current MPI library with MPICH to proceed.

```bash
   user@host[~]  module list

   Currently Loaded Modules:
     1) autotools   2) prun/1.2   3) gnu8/8.3.0   4) openmpi3/3.1.3   5) ohpc

  user@host[~] module spider mpich

  ------------------------------------------------------
  mpich:
 ------------------------------------------------------
    Description:
      MPICH MPI implementation

     Versions:
        mpich/3.2.1
        mpich/3.3

------------------------------------------------------
  For detailed information about a specific "mpich" module (including how to load the modules) use the full name.
  For example:

     $ module spider mpich/3.3
------------------------------------------------------

user@host[~]  module load mpich/3.3
Lmod has detected the following error: You can only have one MPI module loaded at a time.
You already have openmpi3 loaded.
To correct the situation, please execute the following command:

  $ module swap openmpi3 mpich/3.3


While processing the following module(s):
    Module fullname  Module Filename
    ---------------  ---------------
    mpich/3.3        /opt/ohpc/pub/moduledeps/gnu8/mpich/3.3


 user@host[~]  module swap openmpi3 mpich/3.3
   ```

3. Compile the C source into a binary executable file.

   ```bash
   mpicc -o hello_world_c hello_world.c
   ```

4. Use `ls -al` to verify the presence of the `hello_world_c` binary in your working directory.

With the C code compiled into a binary \(`hello_world_c`\), we can now schedule and run the job on our compute nodes.

## Step 4: Run the Job

1. Before proceeding, please check the path/directory as your SLURM script and C binary. Use `ls -al` to confirm their presence.
2. Use `sbatch` to schedule your batch job in the queue.

   ```bash
   sbatch mpi-test.slurm
   ```

   This command will automatically queue your job using SLURM and produce a job number \(shown below\). You can check the status of your job at any time with the `squeue` command.

   ```bash
   squeue -u $USER
   ```

   You can also stop your job at any time with the `scancel` command.

   ```bash
   scancel <job_ID>
   ```

3. View your results.  
    Once your job completes, SLURM will produce two output/data files. These output/data files, unless otherwise specified in the SLURM script, are placed in the same path as your binary.  
    One file \(`MPItest-<jobnumber>.out`\) contains the results of the binary you just executed, and the other \(`MPItest-<jobnumber>.err`\) contains any errors that occurred during execution. Please replace  "<jobnumber\> with your job number.  
    You can view the contents of these files using the `more` command followed by the file name.  

   ```bash
   more mpi_hello_world_c.oXXXXX
   ```

   Your output should look something like this, with one line per processor core \(80 in this case\):

   ```bash
    Hello world from processor compute001, rank 3 out of 80 processors
    Hello world from processor compute002, rank 12 out of 80 processors
    Hello world from processor compute002, rank 31 out of 80 processors
    Hello world from processor compute001, rank 24 out of 80 processors
    .
    .
    .
   ```
4. You have successfully created an MPI code and run it through a batch queue manager!

#### Works Cited

1. Wes Kendall, "MPI Hello World," _MPI Tutorial_, accessed June 14, 2017, [http://mpitutorial.com/tutorials/mpi-hello-world/](http://mpitutorial.com/tutorials/mpi-hello-world/).

#### Additional Examples

* [Working with C++](cpp.md)
* [Working with Fortran](fortran.md)
* [Working with Python](python.md)
* [Working with Makefiles](makefile.md)
