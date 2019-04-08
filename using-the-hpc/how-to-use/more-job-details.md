# More Job Details

AVAILABLE QUEUES:

```bash
iserbt-local@openhpc[~/ResearchTools/startup]  sinfo
PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
stdmemq      up 2-00:00:00      8   idle compute[001-008]
bigmemq      up 2-00:00:00      1   idle bigmem001
debugq       up    2:00:00      2   idle gpu[001-002]
gpuq         up 2-00:00:00      2   idle gpuv100[001-002]
```

Description:
```
Queue    | QOS   | Max Walltime | Priority | Description
-------- | ----- | ------------ | -------- | -----------------------------------------------------------------
stdmemq  | std   | 48 hours     | avg    | the 8 nodes in this queue are the best choice for most jobs
bigmemq  | std   | 4 hours      | avg    | this node with 80 cores and 1.5TB of memory is ideal for large SMP jobs with large memory demands
gpuq     | std   | 48 hours     | avg    | this partition is exclusively for jobs utilizing our NVIDIA Tesla V100 GPUs
debugq   | devel | 2 weeks      | high   | the 2 nodes in this partition are for short jobs (< 2 hr) and quick development tests

## Example Submission Scripts:

STDMEMQ:

```text
#PBS -N jobname
#PBS -A group
#PBS -q batch
#PBS -W group_list=group_name
#PBS -l qos=burst
#PBS -l nodes=16:ppn=16
#PBS -l walltime=1:00:00
```

STANDARD CPU QUEUE:

```text
#PBS -N jobname
#PBS -A group
#PBS -q high_mem
#PBS -W group_list=group_name
#PBS -l qos=std
#PBS -l nodes=16:ppn=16
#PBS -l walltime=1:00:00
```

GPU QUEUE:

```text
#PBS -N jobname
#PBS -A group
#PBS -q gpu_ssd
#PBS -W group_list=group_name
#PBS -l qos=std
#PBS -l nodes=2:ppn=16
#PBS -l walltime=1:00:00
```

## Scheduling Batch Jobs

Batch scripts, or job submission scripts, are the mechanism by which a user submits and configures a job for execution. A batch script is simply a shell script which contains:

* Commands that can be interpreted by batch scheduling software (e.g. PBS)
* Commands that can be interpreted by a shell

The batch script is submitted to the batch scheduler where it is parsed. Based on the parsed data, the batch scheduler places the script in the scheduler queue as a batch job. Once the batch job makes its way through the queue, the script will be executed on a service node within the set of allocated computational resources.

 **Sections of a Batch Script** - Batch scripts are parsed into the following three sections:

1. The Interpreter Line: The first line of a script can be used to specify the script’s interpreter. This line is optional. If not used, the submitter's default shell will be used. The line uses the "hash-bang-shell" syntax: `#!/path/to/shell`
2. The Scheduler Options Section: The batch scheduler options are preceded by `#PBS`, making them appear as comments to a shell. PBS will look for `#PBS` options in a batch script from the script’s first line through the first non-comment line. A comment line begins with `#`. `#PBS` options entered after the first non-comment line will not be read by PBS.
3. The Executable Commands Section: The shell commands follow the last `#PBS` option and represent the main content of the batch job. If any `#PBS` lines follow executable statements, they will be ignored as comments.

The execution section of a script will be interpreted by a shell and can contain multiple lines of executable invocations, shell commands, and comments. When the job's queue wait time is finished, commands within this section will be executed on a service node (sometimes called a "head node") from the set of the job's allocated resources. Under normal circumstances, the batch job will exit the queue after the last line of the script is executed.

## An Example Batch Script:

```text
#!/bin/bash
#PBS -A group
#PBS -N username
#PBS -l nodes=16:ppn=8
#PBS -l walltime=4:00:00
#PBS -W group_list=group_name
#PBS -q high_mem
#PBS -j oe
#PBS -m abe
#PBS -M your_email@example.com
#PBS -V
#PBS -o o.log
#PBS -e e.log
#PBS -S /bin/bash
```

The following table summarizes frequently-used options to PBS:

Option | Use                | Description
------ | ------------------ | ------------------------------------------------------------------------------
-A     | #PBS -A            | Causes the job time to be charged to ???. The account string is typically composed of the three letters followed by three digits and optionally followed by a subproject identifier. The utility showproj can be used to list your valid assigned project ID(s). This option is required by all jobs.
-l     | #PBS -l nodes=     | Maximum number of compute nodes. Jobs cannot request partial nodes.
       | #PBS -l ppn=       | Processors per nodes.
       | #PBS -l walltime=  | maximum wall-clock time, is in the format HH:MM:SS.
       | #PBS -l partition= | Allocates resources on specified partition.
-o     | #PBS -o            | Writes standard output to ??? instead of .o$PBS_JOBID, $PBS_JOBID is an environment variable created by PBS that contains the PBS job identifier.
-e     | #PBS -e            | Writes standard error to ??? instead .e$PBS_JOBID
-j     | #PBS -j {oe, eo}   | Combines standard output and standard error into the standard error file (eo) or the standard out file (oe).
-m     | #PBS -m a          | Sends email to the submitter when the job aborts.
       | #PBS -m b          | Sends email to the submitter when the job begins.
       | #PBS -m e          | Sends email to the submitter when the job ends.
-M     | #PBS -M            | Specifies email address to use for -m options.
-N     | #PBS -N            | Sets the job name to ??? instead of the name of the job script.
-S     | #PBS -S            | Sets the shell to interpret the job script.
-q     | #PBS -q            | Directs the job to the specified queue. This option is not required to run in the default queue on any given system.
-V     | #PBS -V            | Exports all environment variables from the submitting shell into the batch job shell. Not recommended because the login nodes differ from the service nodes, using the `-V` option is not recommended. Users should create the needed environment within the batch job.
-X     | #PBS -X            | Enables X11 forwarding. The `-X` PBS option should be used to tunnel a GUI from an interactive batch job.


To submit job to the queue:

`qsub job_submission_script`

To check status of the jobs in the queue:

`qstat -u username`

PBS sets multiple environment variables at submission time. The following PBS variables are useful within batch scripts:

Variable       | Description
-------------- | -----------------------------------------------------------------------------------------------------------------------
$PBS_O_WORKDIR | The directory from which the batch job was submitted. By default, a new job starts in your home directory.
$PBS_JOBID     | The job's full identifier. A common use for PBS_JOBID is to append the job's ID to the standard output and error files.
$PBS_NUM_NODES | The number of nodes requested.
$PBS_JOBNAME   | The job name supplied by the user.
$PBS_NODEFILE  | The name of the file containing the list of nodes assigned to the job. Used sometimes on non-Cray clusters.
