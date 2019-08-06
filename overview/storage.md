# Storage

The storage on the HPC cluster is comes in three forms -- globally accessible permanent storage \(`/home`, `$HOME`\), globally accessible temporary storage \(`/globalscratch`, `$GLOBALSCRATCH`\), and node-local temporary storage \(`/localscratch`, `$LOCALSCRATCH`, `$SCRATCH`\).

| Storage Area | Path | Env variable | Purpose |
| :--- | :--- | :--- | :--- |
| User Home | /home/$USER | $HOME | Long-term data for routine access |
| User Global Scratch | /globalscratch/$USER | $GLOBALSCRATCH | Short-term globally accessible data for fast, batch-job access |
| User Local Scratch | /localscratch/$USER | $SCRATCH, $LOCALSCRATCH | Fast node-local read/write access during a batch job |

## USER Home

The 512TB `/home` partition is NFS-shared from a Dell NSS-HA storage server to the login/head node as well as all compute nodes. Permanent, long-term data should be stored here, but other data on which your computations will be done must be moved to the faster global \(`/globalscratch`\) or local \(`/localscratch`\) directories at run time. Please refrain from running calculations with large I/O footprint in this partition because they will compromise the whole cluster. The environmental variable `$HOME` refers to users home directories \(`/home/$USER`\). There is a disk usage quota of 100GB per faculty/staff and 10GB per students. If you need storage exceeding this quota, please request an increase by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20/home%20storage%20limit%20).

## USER SCRATCH

### Global

The 38TB `/globalscratch` is a fast, temporary storage that is NFS-shared on the login/head node as well as all compute nodes. It is composed of 24 1.6TB NVMe SSD drives merged striped \(RAID0\) to form one big partition. Users with jobs that span multiple nodes, or intermediate data output exceeding 300GB are encouraged to use this partition for temporary storage. While there is currently no limit on how much of the storage users take up in this partition, files stored here are periodically purged to make sure there is always sufficient space for running calculations.

### Node-local

The `/localscratch` is the local temporary space on each compute node. It is not directly accessible from other nodes. This partition is a temporary space that is strictly local to individual compute nodes. Users running calculations contained within individual nodes whose disk usage won't exceed 300GB on most compute nodes and 600GB on the `bigmem` node are strongly encouraged to use this space.

