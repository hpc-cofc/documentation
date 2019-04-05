# Storage

The storage on the HPC cluster is comes in three forms -- globally accessible permanent storage (<code>/home</code>, <code>$HOME</code>), globally accessible temporary storage (<code>/globalscratch</code>, <code>$GLOBALSCRATCH</code>), and node-local temporary storage (<code>/localscratch</code>, <code>$LOCALSCRATCH</code>, <code>$SCRATCH</code>).

| Storage Area | Path | Env variable | Purpose |
| :--- | :--- | : --- | :--- |
| User Home | /home/$USER | $HOME | Long-term data for routine access |
| User Global Scratch | /globalscratch/$USER | $GLOBALSCRATCH  | Short-term globally accessible data for fast, batch-job access|
| User Local Scratch | /localscratch/$USER | $SCRATCH, $LOCALSCRATCH | Fast node-local read/write access during a batch job |

## USER Home

The 512TB <code>/home</code> partition is NFS-shared from a Dell NSS-HA storage server to the login/head node as well as all compute nodes. Permanent, long-term data should be stored here, but other data on which your computations will be done must be moved to the faster global (<code>/globalscratch</code>) or local (<code>/localscratch</code>) directories at run time. Please refrain from running calculations with large I/O footprint in this partition because they will compromise the whole cluster. The environmental variable <code>$HOME</code> refers to users home directories (<code>/home/$USER</code>). There is a disk usage quota of 100GB per faculty/staff and 10GB per students. If you need storage exceeding this quota, please request an increase by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20/home%20storage%20limit%20).

## USER SCRATCH
### Global

The 35TB <code>/globalscratch</code> is a fast, temporary storage that is NFS-shared on the login/head node as well as all compute nodes. It is composed of 24 1.6TB NVMe SSD drives merged striped (RAID0) to form one big partition. Users with jobs that span multiple nodes, or intermediate data output exceeding 300GB are encouraged to use this partition for temporary storage. While there is currently no limit on how much of the storage users take up in this partition, files stored here are periodically purged to make sure there is always sufficient space for running calculations.

### Node-local
The <code>/localscratch</code> is the local temporary space on each compute node. It is not directly accessible from other nodes.
This partition is a temporary space that is strictly local to individual compute nodes. Users running calculations contained within individual nodes whose disk usage won't exceed 300GB on most compute nodes and 600GB on the <code>bigmem</code> node are strongly encouraged to use this space.

<!--

### PROJECT SHARE

### LOCAL SCRATCH STORAGE

### Data Retention, Purge, & Quotas

### SUMMARY

### DATA STORAGE RESOURCES

-->
<!--
The ADC Cluster provides an array of data storage platforms, each designed with a particular purpose in mind. Storage areas are broadly divided into two categories: those intended for user data and those intended for project data. Within each of the two categories, we provide different sub-areas, each with an intended purpose:

| Storage Area | Path | Purpose |
| :--- | :--- | :--- |
| User Home | /home/$USER | Long-term data for routine access |
| User Scratch | /lustre/or-myst/cad-right/$USER | Short-term project data for fast, batch-job access that is not shared |
| Project Share | /lustre/or-myst/cad-right/proj-shared/$USER | Short-term project data for fast, batch-job access that's shared with other project members |
| World Share | /lustre/or-myst/cad-right/world-shared/$USER | Short-term project data for fast, batch-job access that is shared globally |
| Local Scratch | $localscratch | Fast read/write access during a batch job |
| User Temp | /data/adc/stratus/ | Long term storage of data not currently in use \(Currently, only accessible using command adc\_xfer\) |
| User Archive | HPSS \(if applicable\) | Placeholder |

### USER HOME

Home directories for each user are NFS-mounted on all CCLA Cluster systems and are intended to store long-term, frequently-accessed user data. User Home areas are not backed up. This file system does not generally provide the input/output \(I/O\) performance required by most compute jobs, and is not available to compute jobs on most systems. See the section [Data Retention, Purge, & Quota Summary](https://github.com/Doane-CCLA/docs/tree/6aa8e86be5b614a863272788de3d9c0182ee56c9/HPC/HPC-5-data-transfer.md#Retention) for more details on applicable quotas, backups, purge, and retention timeframes.

### USER SCRATCH

Project members get an individual User Scratch directory; these reside in the high-capacity Lustre® file system on large, fast disk areas intended for global \(parallel\) access to temporary/scratch storage. Because of the scratch nature of the file system, it is not backed up and files are automatically purged on a regular basis. Files should not be retained in this file system for long, but rather should be migrated to HPSS Archive space as soon as the files are not actively being used. If a file system associated with your User Scratch directory is nearing capacity, the CCLA Cluster Support may contact you to request that you reduce the size of your Member scratch directory. See the section [Data Retention, Purge, & Quota Summary](https://github.com/Doane-CCLA/docs/tree/6aa8e86be5b614a863272788de3d9c0182ee56c9/HPC/HPC-5-data-transfer.md#Retention) for more details on applicable quotas, backups, purge, and retention timeframes.

### PROJECT SHARE

Individual Project Share directories reside in the high-capacity Lustre file system on large, fast disk areas intended for global \(parallel\) access to temporary/scratch storage. Because of the scratch nature of the file system, it is not backed up. If a file system associated with Project Share storage is nearing capacity, the CCLA Cluster Support may contact the PI of the project to request that he or she reduce the size of the Project scratch directory. See the section [Data Retention, Purge, & Quota Summary](https://github.com/Doane-CCLA/docs/tree/6aa8e86be5b614a863272788de3d9c0182ee56c9/HPC/HPC-5-data-transfer.md#Retention) for more details on applicable quotas, backups, purge, and retention timeframes.

### WORLD SHARE

Each project has a World Share directory that resides in the high-capacity Lustre file system on large, fast disk areas intended for global \(parallel\) access to temporary/scratch storage. Because of the scratch nature of the file system, it is not backed up. If a file system associated with World Share storage is nearing capacity, the CCLA Cluster may contact the PI of the project to request that he or she reduce the size of the World Work directory. See the section [Data Retention, Purge, & Quota Summary](https://github.com/Doane-CCLA/docs/tree/6aa8e86be5b614a863272788de3d9c0182ee56c9/HPC/HPC-5-data-transfer.md#Retention) for more details on applicable quotas, backups, purge, and retention timeframes.

### LOCAL SCRATCH STORAGE

A fast solid state disk \(SSD\) area intended for parallel access to temporary storage in the form of scratch directories. This area is local to the computational node. This directory is, for example, intended to hold temporary and intermediate output generated by a user’s job. This is a run time only file system which is created at the start of a batch job and is purged at the end of the job. Files should not be retained in this file system and should be migrated to Lustre scratch or archival storage before finishing the job.

Path for local scratch storage is available during job runtime via environment variable `$localscratch`. Variable `$localscratch` typically has the form `/localscratch/tmp.$USER.$PBS_JOBID.or-condo-pbs01` and is specific to the user and to the scheduled job.

### PROJECT STORAGE \(WARP\)

A NFS area intended for temporary data storage for moving data off the Lustre file system. This area is local to the computational node. This directory is, for example, intended to hold temporary and intermediate output generated by a user’s job. This is a run time only file system which is created at the start of a batch job and is purged at the end of the job. Files should not be retained in this file system and should be migrated to Lustre scratch or archival storage before finishing the job.

## Data Retention, Purge, & Quotas

### SUMMARY

The following table details quota, backup, purge, and retention information for each user-centric and project-centric storage area available at the CCLA Cluster.

### DATA STORAGE RESOURCES

| Area | Path | Type | Permissions | Quota | Backups | Purged | Retention |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| User Home | /home/$USER | NFS | User-controlled | 10 GB | No | No | NA |
| User Scratch | /lustre/or-myst/cad-right/$USER | Lustre | 700 | TBD | No | No | TBD Days |
| Project Share | /lustre/or-myst/cad-right/proj-share | Lustre | 770 | TBD | No | No | TBD Days |
| World Share | /lustre/or-myst/cad-arm/world-share | Lustre | 775 | TBD | No | No | TBD Days |
| Local Scratch | /lustre/or-myst/cad-right/scratch | Lustre | 770 | TBD | No | No | TBD Days |
-->
