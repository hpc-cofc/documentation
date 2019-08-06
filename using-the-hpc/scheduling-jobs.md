# Schedule Jobs

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

```bash
squeue
```

To list your jobs:

```bash
squeue -u $USER
```

To obtain the status of a job, run the following command using the job's ID number \(this is provided at time of job submission\).

```bash
squeue -j JOB_ID
```

You can also use `checkjob job_ID` to show the current status of the job.

### Submitting a job

To submit a job, use the `sbatch` command, followed by the name of your submission file. A Job ID will be provided. You may want to make note of the ID for later use.

```bash
sbatch your_script
```

### Deleting a job

**Note:** Be aware that deleting a job cannot be undone. Double check the job ID before deleting a job.

Users can delete their jobs by typing the following command.

```bash
scancel JOB_ID
```

To delete all the jobs of a user:

```bash
scancel -u $USER
```

### Overview of resources

The `sinfo` command gives an overview of what resources are in each partition/queue and what their status is. It should inform your decisions on how you structure your jobs and what partition you should submit them to.

```bash
sinfo
```

You can format that output in a more concise form:

```bash
sinfo -o "%20P %5a %.10l %16F"
```

### Status of past and current jobs

The `sacct` command gives some accounting details on past and current jobs.

```bash
sacct
```

You can format that output in a more detailed form:

```bash
sacct --format=jobid,user,jobname,partition,end,Elapsed,State
```

## SLURM environmental variables

When a SLURM job is scheduled to run, some relevant information about the job such as the names of the nodes it is running on, the number of cores, the working directory ... etc ... are saved as environmental variables. Users can invoke these environmental variables in their job submission scripts.

Below is a list of the most common SLURM environmental variables including with a brief description from [UMD's HPC page](https://www.glue.umd.edu/hpcc/help/slurmenv.html).

| SLURM Variable Name | Description | Example values | PBS/Torque analog |
| :--- | :--- | :--- | :--- |
| $SLURM\_JOB\_ID | Job ID | 5741192 | $PBS\_JOBID |
| $SLURM\_JOBID | Deprecated. Same as SLURM\_JOB\_ID |  |  |
| $SLURM\_JOB\_NAME | Job Name | myjob | $PBS\_JOBNAME |
| $SLURM\_SUBMIT\_DIR | Submit Directory | /home/user/testdir | $PBS\_O\_WORKDIR |
| $SLURM\_JOB\_NODELIST | Nodes assigned to job | compute\[001-003\] | cat $PBS\_NODEFILE |
| $SLURM\_SUBMIT\_HOST | Host submitted from | login-hpc.cofc.edu | $PBS\_O\_HOST |
| $SLURM\_JOB\_NUM\_NODES | Number of nodes allocated to job | 2     $PBS\_NUM\_NODES |  |
| $SLURM\_CPUS\_ON\_NODE | Number of cores/node | 8,3 | $PBS\_NUM\_PPN |
| $SLURM\_NTASKS | Total number of cores for job | 11 | $PBS\_NP |
| $SLURM\_NODEID | Index to node running on relative to nodes assigned to job | 0 | $PBS\_O\_NODENUM |
| $SLURM\_LOCALID | Index to core running on within node | 4 | $PBS\_O\_VNODENUM |
| $SLURM\_PROCID | Index to task relative to job | 0 | $PBS\_O\_TASKNUM - 1 |

### Related Information

* [MPI Example](execute-a-job/)
