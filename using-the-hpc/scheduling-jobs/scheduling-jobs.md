# SLURM

## Managing Jobs

HPC utilizes SLURM to manage jobs that users submit to various queues on a computer system. Each queue represents a group of resources with attributes necessary for the queue's jobs. You can see the list of queues that HPC has by typing `sinfo`. **stdmemq** is the default partition/queue.

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

### Related Information

* [MPI Example](execute-a-job/)

