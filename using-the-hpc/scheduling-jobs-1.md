# Schedule Jobs using SLURM

SLURM is a powerful job scheduler that enables optimal use of an HPC cluster of any size. It takes certain information about the resource requirements of a calculations and send that calculation to run on a compute node\(s\) that satisfy that criteria. It also ensures that the HPC cluster is used fairly among all users. 

## Compute Nodes

The compute nodes have the following resources:

*  S = CPU sockets
* C = Cores per CPU
* CORES = Total number of coresPU cores

```sql
NODELIST    NODES    PARTITION       STATE CORES  S:C:T MEMORY
bigmem001       1    scavengeq       mixed   80   4:20:1 1536000
compute001      1    scavengeq       mixed   40   2:20:1 192000
compute002      1    scavengeq       mixed   40   2:20:1 192000
compute003      1    scavengeq       mixed   40   2:20:1 192000
compute004      1    scavengeq       mixed   40   2:20:1 192000
compute005      1    scavengeq       mixed   40   2:20:1 192000
compute006      1    scavengeq       mixed   40   2:20:1 192000
compute007      1    scavengeq       mixed   40   2:20:1 192000
compute008      1    scavengeq       mixed   40   2:20:1 192000
gpu001          1    scavengeq       mixed   40   2:20:1 192000
gpu002          1    scavengeq       mixed   40   2:20:1 192000
gpuv100001      1    scavengeq       mixed   24   2:12:1 192000
gpuv100002      1    scavengeq       mixed   24   2:12:1 192000
loginbk         1    scavengeq       mixed   22   2:11:1 192000
```

These compute nodes belong to different queues or partitions :

```sql
PARTITION    AVAIL  TIMELIMIT  NODES  STATE NODELIST
stdmemq         up 2-00:00:00      13    mix compute[001-008],gpu[001-002],loginbk,gpuv[100001-100002]
stdmemq-long    up 4-00:00:00      2    mix bigmem001,gpu002
bigmemq         up 2-00:00:00      1    mix bigmem001
gpuq            up 4-00:00:00      2    mix gpuv[100001-100002]
debugq          up    2:00:00      5    mix gpu[001-002],gpuv[100001-100002],loginbk
scavengeq       up 2-00:00:00      13    mix bigmem001,compute[001-008],gpu[001-002],loginbk
```

## Queues/Partitions

The compute nodes in the cluster are assigned to one or more queues or partitions. Users submit their jobs to one partition and the job runs on a compute node\(s\) that belongs in that partition.  You can look at the partitions and the status of the compute resources under each using the `sinfo` command.

```sql
user@host[~]:   sinfo -o "%20P %5a %.10l %16F"
PARTITION            AVAIL  TIMELIMIT NODES(A/I/O/T)
stdmemq*             up    2-00:00:00 0/10/0/10
stdmemq-long         up    4-00:00:00 1/2/0/3
bigmemq              up    2-00:00:00 1/0/0/1
gpuq                 up    4-00:00:00 1/1/0/2
debugq               up       2:00:00 1/3/0/4
scavengeq            up    1-00:00:00 2/11/0/13
```

You may submit jobs that require up to 48 hours of processing time and 8 nodes to the standard default queue. If your jobs require more computing resources than the defined Linux resource limit, please send an email to [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20walltime%20limit%20).

* **debugq**  - this queue shares two compute nodes with the `stdmemq` queue and it is intended for testing quick jobs before submitting production runs to the `stdmemq` queue. Run times in this queue are limited to 2 hours and 2 nodes.
* **stdmemq** - this is the default queue containing 10 compute nodes with 40 cores, 192GB of RAM and 300GB SSD storage each. Run times in this queue are limited to 48 hours unless you request an extension by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20walltime%20limit%20).
* **stdmemq-long** - this queue is the same as the `stdmemq` , except run times in this queue are extended to a maximum of 96 hours unless you request an extension by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20walltime%20limit%20).
* **bigmemq** - this queue is intended to provide access to our large node which has 80 cores, 1.5TB of RAM and 600GB SSD. Run times in this queue are limited to 24 hours and 1 node.
* **gpuq** - this queue is intended to provide access to two nodes each with 1 NVIDIA Tesla V100 GPU, 24 cores, 192GB of RAM and 300GB SSD. Run times in this queue are limited to 96 hours and 1 node.

The HPC cluster is a shared computing resource. Jobs with a long wait or sleep loop jobs are not allowed on the cluster, as this wastes valuable computing time that could be used by other researchers. Any jobs with a long wait or that contain a sleep loop may be terminated without advance notice. Additionally, any processes that may create performance or load issues on the head node or interfere with other users’ jobs may be terminated. This includes compute jobs running on the compute nodes.

## Batch Submission Script

A typical batch submission script file looks like this:

```bash
#!/bin/bash

#SBATCH -p stdmemq          # Submit to 'stdmemq' Partitiion or queue
#SBATCH -J MPItest          # Name the job as 'MPItest'
#SBATCH -o MPItest-%j.out   # Write the standard output to file named 'jMPItest-<job_number>.out'
#SBATCH -e MPItest-%j.err   # Write the standard error to file named 'jMPItest-<job_number>.err'
#SBATCH -t 0-12:00:00        # Run for a maximum time of 0 days, 12 hours, 00 mins, 00 secs
#SBATCH --nodes=1            # Request N nodes
#SBATCH --ntasks-per-node=20 # Request n cores or task per node
#SBATCH --mem-per-cpu=4GB   # Request 4GB RAM per core
#SBATCH --mail-type=ALL      # Send email notification at the start and end of the job
#SBATCH --mail-user=<user>@cofc.edu  # Send email notification to this address

module list                 # will list modules loaded by default. In our case, it will be GNU8 compilers and OpenMPI3 MPI libraries
module swap openmpi3 mpich  # swap the MPI library from the default 'openmpi3' to 'mpich'.
module list                 # will list modules loaded; we'll just use this to check that the modules we selected are indeed loaded
pwd                         # prints current working directory
date                        # prints the date and time

mpirun hello_world_c        # run the MPI job
```

You can always type `man sbatch` to see all the SLURM batch submission options. Below is an explanation of the options used above.

| - | Option | Description |
| :--- | :--- | :--- |
| SBATCH | -p, `--partition=<partition>` | Submit the job to `<partition>` queue |
| SBATCH | -J, `--job-name=<jobname>` | Name the job as `<jobname>` |
| SBATCH | -o, `--output=<filename>` | Write the job's standard output to the file name named `<filename>` |
| SBATCH | -e, `--error=<filename>` | Write the job's standard error messages to the file name named `<filename>` |
| SBATCH | `--mail-user=<e-mail_address>` | Notify user by email when certain event types occur, as specified by the `--mail-type=<type>` option. |
| SBATCH | `--mail-type=<type>` | Notify user by email when certain event types occur. `<type>=ALL` notifies upon the start, end or failing of the job. `<type>=END` only notified the user at the end. |
| SBATCH | -N, `--nodes=<n>` | Request that `n` nodes be allocated to this job. |
| SBATCH | `--ntasks-per-node=<ntasks>` | Request that `ntasks` be started on each node. |
| SBATCH | `--mem=<size[units]>` | Specify the real memory required per node in the proper unit. |
| SBATCH | `--mem-per-cpu=<size[units]>` | Specify memory per **core**. 4GB is a reasonable number. |
| SBATCH | -t, `--time=<time>` | Maximum run time for your job in the format `D-HH:MM:SS` |

The cluster utilizes SLURM to manage jobs that users submit to various queues on a computer system. Each queue represents a group of resources with attributes necessary for the queue's jobs. You can see the list of queues that HPC has by typing `sinfo`. **stdmemq** is the default partition/queue.

### Common Commands

The table below gives a short description of the most used SLURM commands.

| Command | Description |
| :--- | :--- |
| squeue | reports the state of jobs \(it has a variety of filtering, sorting, and formatting options\), by default, reports the running jobs in priority order followed by the pending jobs in priority order |
| sbatch | submit a job script for later execution \(the script typically contains one or more srun commands to launch parallel tasks\) |
| scancel | cancel a pending or running job |
| sinfo | reports the state of partitions and nodes managed by SLURM \(it has a variety of filtering, sorting, and formatting options\) |
| sacct | report job accounting information about active or completed jobs |
| srun | used to submit a job for execution in real time |
| salloc | allocate resources for a job in real time \(typically used to allocate resources and spawn a shell, in which the srun command is used to launch parallel tasks\) |

**Note:** Do not run jobs on the login nodes. All jobs launched from those nodes will be terminated without notice.

### Listing jobs

To list all jobs:

```sql
user@host[~]:   squeue
 JOBID  PARTITION  NAME      USER   STATE    TIME        TIME_LIMI   CPUS  NODES  NODELIST(REASON)
4340   gpuq       testjob1  user1  RUNNING  2-03:06:55  4-00:00:00  2     1      gpu1
4349   stdmemq    testjob2  user2  RUNNING  1:36:09     2-00:00:00  2     1      compute1
4347   bigmemq    testjob3  user2  RUNNING  18:34:07    2-00:00:00  40    1      bigmem1
```

To list your jobs:

```sql
user@host[~]:   squeue -u $USER
```

To obtain the status of a job, run the following command using the job's ID number \(this is provided at time of job submission\).

```sql
user@host[~]:   squeue -j JOB_ID
```

You can also use `checkjob job_ID` to show the current status of the job.

### Submitting a job

To submit a job, use the `sbatch` command, followed by the name of your submission file. A Job ID will be provided. You may want to make note of the ID for later use.

```sql
user@host[~]:   sbatch your_script.slurm
Submitted batch job 4359
```

### Deleting a job

**Note:** Be aware that deleting a job cannot be undone. Double check the job ID before deleting a job.

Users can delete their jobs by typing the following command.

```sql
user@host[~]:   scancel JOB_ID
```

To delete all the jobs of a user:

```sql
user@host[~]:   scancel -u $USER
```

### Overview of resources

The `sinfo` command gives an overview of what resources are in each partition/queue and what their status is. It should inform your decisions on how you structure your jobs and what partition you should submit them to.

```sql
user@host[~]:   sinfo
PARTITION    AVAIL  TIMELIMIT  NODES  STATE NODELIST
stdmemq*        up 2-00:00:00      1    mix bigmem1
stdmemq*        up 2-00:00:00     10    mix compute[1-8],gpu[1-2]
stdmemq-long    up 4-00:00:00      1    mix bigmem1
bigmemq         up 2-00:00:00      1    mix bigmem1
gpuq            up 4-00:00:00      1    mix gpuv1001
gpuq            up 4-00:00:00      1   idle gpuv1002
debugq          up    2:00:00      1    mix gpuv1001
debugq          up    2:00:00      3   idle gpu[1-2],gpuv1002
scavengeq       up 1-00:00:00      2    mix bigmem0,gpuv1001
```

You can format that output in a more concise form:

```sql
user@host[~]:   sinfo -o "%20P %5a %.10l %16F"
PARTITION            AVAIL  TIMELIMIT NODES(A/I/O/T)
stdmemq*             up    2-00:00:00 1/10/0/11
stdmemq-long         up    4-00:00:00 1/2/0/3
bigmemq              up    2-00:00:00 1/0/0/1
gpuq                 up    4-00:00:00 1/1/0/2
debugq               up       2:00:00 1/3/0/4
scavengeq            up    1-00:00:00 2/11/0/13
```

### Status of past and current jobs

The `sacct` command gives some accounting details on past and current jobs.

```sql
user@host[~]:   sacct
4359         jredo-0.x+    bigmemq     (null)          0  COMPLETED      0:0
4360         jredo-0.x+    bigmemq     (null)          0  CANCELLED      0:0
.
.
.
```

You can format that output in a more detailed form:

```sql
user@host[~]:   sacct --format=jobid,user,jobname,partition,end,Elapsed,State
4359          user jredo-0.x+    bigmemq 2019-08-07T15:03:15   00:00:10  COMPLETED
4360          user jredo-0.x+    bigmemq 2019-08-07T15:03:42   00:00:05  CANCELLED
```

## SLURM environmental variables

When a SLURM job is scheduled to run, some relevant information about the job such as the names of the nodes it is running on, the number of cores, the working directory ... etc ... are saved as environmental variables. Users can invoke these environmental variables in their job submission scripts.

Below is a list of the most common SLURM environmental variables including with a brief description from [UMD's HPC page](https://www.glue.umd.edu/hpcc/help/slurmenv.html).

| SLURM Variable Name | Description | Example values | PBS/Torque analog |
| :--- | :--- | :--- | :--- |
| $SLURM\_JOB\_ID | Job ID | 5741192 | $PBS\_JOBID |
| $SLURM\_JOB\_NAME | Job Name | myjob | $PBS\_JOBNAME |
| $SLURM\_SUBMIT\_DIR | Submit Directory | /home/user/testdir | $PBS\_O\_WORKDIR |
| $SLURM\_JOB\_NODELIST | Nodes assigned to job | compute\[1-3\] | cat $PBS\_NODEFILE |
| $SLURM\_SUBMIT\_HOST | Host submitted from | login-hpc.cofc.edu | $PBS\_O\_HOST |
| $SLURM\_JOB\_NUM\_NODES | Number of nodes allocated to job | 2     $PBS\_NUM\_NODES |  |
| $SLURM\_CPUS\_ON\_NODE | Number of cores/node | 8,3 | $PBS\_NUM\_PPN |
| $SLURM\_NTASKS | Total number of cores for job | 11 | $PBS\_NP |
| $SLURM\_NODEID | Index to node running on relative to nodes assigned to job | 0 | $PBS\_O\_NODENUM |
| $SLURM\_LOCALID | Index to core running on within node | 4 | $PBS\_O\_VNODENUM |
| $SLURM\_PROCID | Index to task relative to job | 0 | $PBS\_O\_TASKNUM - 1 |

For a more complete list of SLURM environmental variables, please check [here](https://slurm.schedmd.com/sbatch.html#lbAJ).

### Related Information

* [MPI Example](scheduling-jobs/execute-a-job/)

