# Policies

Users of the high-performance computing \(HPC\) system must abide by [CofC's IT policies](http://policy.cofc.edu/policy.php#it) as well those outlined below specifically for HPC. These HPC usage policies have been adapted from [USC](https://hpcc.usc.edu/support/accounts/hpcc-policies/) and reflect standards practiced at most institutions.

## Account Creation

* Faculty and staff can request accounts by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Requesting%20new%20faculty/staff%20account) or filling out a [service request](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085).
* Students are eligible for accounts upon endorsement or sponsorship by their faculty/staff mentor/advisor. Their faculty/staff mentor/advisor should send an email request to [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Requesting%20new%20student%20account) on their behalf to initiate the account creation process.

## Account Security

Every user will have their own login credentials that they must guard with caution. Sharing of accounts and credentials is strictly forbidden. If a user is deemed to have shared their credentials, their account will be suspended immediately.

## Account Lifecycle

* Faculty and staff accounts will remain active as long as they are at the CofC unless \(1\) they request that it be terminated or \(2\) the account is inactive for longer than two years.
* Students accounts will be deactivated whenever any one of these following criteria are met:
  * The student graduates, **OR**
  * The student's faculty/staff mentor indicates that the student no longer needs access to the cluster, **OR**
  * The student's account remains inactive for longer than two years

## Resource Management

### Head Node Process Limit Policy

You are restricted to a small number of processes running in the login/head node because it hosts critical services and is shared with lots of other users simultaneously. Therefore, tasks on the head node are limited to processes that are not long or resource intensive such as file transfers, code compilation, simple pre- and post-processing that can not be performed on the compute nodes using the batch queueing system. Any violations of these rules will result in your processes being terminated, and your account being suspended or revoked upon repeated infractions.

### Computing Resources Limit Policy

You may submit jobs that require up to 48 hours of processing time and 8 nodes to the standard default queue. If your jobs require more computing resources than the defined Linux resource limit, please send an email to [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20walltime%20limit%20).

* **debugq**  - this queue shares two compute nodes with the `stdmemq` queue and it is intended for testing quick jobs before submitting production runs to the `stdmemq` queue. Run times in this queue are limited to 2 hours and 2 nodes.
* **stdmemq** - this is the default queue containing 10 compute nodes with 40 cores, 192GB of RAM and 300GB SSD storage each. Run times in this queue are limited to 48 hours unless you request an extension by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20walltime%20limit%20).
* **bigmemq** - this queue is intended to provide access to our large node which has 80 cores, 1.5TB of RAM and 600GB SSD. Run times in this queue are limited to 24 hours and 1 node.
* **gpuq** - this queue is intended to provide access to two nodes each with 1 NVIDIA Tesla V100 GPU, 24 cores, 192GB of RAM and 300GB SSD. Run times in this queue are limited to 48 hours and 1 node.

The HPC cluster is a shared computing resource. Jobs with a long wait or sleep loop jobs are not allowed on the cluster, as this wastes valuable computing time that could be used by other researchers. Any jobs with a long wait or that contain a sleep loop may be terminated without advance notice. Additionally, any processes that may create performance or load issues on the head node or interfere with other users’ jobs may be terminated. This includes compute jobs running on the compute nodes.

### Storage Resources Limit Policy

The storage on the HPC cluster is comes in three forms -- globally accessible permanent storage \(`/home`, `$HOME`\), globally accessible temporary storage \(`/globalscratch`, `$GLOBALSCRATCH`\), and node-local temporary storage \(`/localscratch`, `$LOCALSCRATCH`, `$SCRATCH`\).

* **/home**  - this 512TB partition is available on the login/head node as well as all compute nodes. Permanent, long-term data should be stored here, but other data on which your computations will be done must be moved to the faster global \(`/globalscratch`\) or local \(`/localscratch`\) directories at run time. Please refrain from running calculations with large I/O footprint in this partition because they will compromise the whole cluster. The environmental variable `$HOME` refers to users home directories \(`/home/$USER`\). There is a disk usage quota of 100GB per faculty/staff and 10GB per students. If you need storage exceeding this quota, please request an increase by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Increasing%20/home%20storage%20limit%20).
* **/globalscratch** - this 35TB partition is a fast, temporary storage that is available on the login/head node as well as all compute nodes. Users with jobs that span multiple nodes, or intermediate data output exceeding 300GB are encouraged to use this partition for temporary storage. While there is currently no limit on how much of the storage users take up in this partition, files stored here are periodically purged to make sure there is always sufficient space for running calculations.
* **/localscratch** - this partition is a temporary space that is strictly local to individual compute nodes. Users running calculations contained within individual nodes whose disk usage won't exceed 300GB on most compute nodes and 600GB on the `bigmem` node are strongly encouraged to use this space.

## Acknowledgement of CofC HPC Usage

Please acknowledge in your publications and presentations the role that CofC's HPC resources have played in your research and teaching. We appreciate your conscientiousness in this matter. Acknowledgement and pre-publication notification helps

* communicate the role HPC plays on campus teaching and research
* encourage more faculty, students and staff to incorporate HPC into their teaching and research
* justify CofC's investment in HPC
* ensure continued funding and support to keep HPC resources available and growing in the future

### Reporting success stories

Please alert our [IT communications department](mailto:drinkuthkh@cofc.edu) or [HPC team](mailto:hpc@cofc.edu) about papers and presentations that utilized CofC's HPC resources and personnel. Some of these success stories will be highlighted in IT's communication as well as other campus publications.

### Publications, Presentations and Other Products

Any publications, presentations, websites, patents and other products resulting from work done on CofC HPC machines should include the following citation:

> "Computation for the work described in this product was supported by the College of Charleston’s High Performance Computing \(HPC\) resources \([https://hpc.cofc.edu](https://hpc.cofc.edu)\)."

Copies of published papers acknowledging HPC should be submitted for inclusion on the HPC project website, under the [publications page](https://hpc.cofc.edu/publications) as well as the [CofC Research and Grants Administration Office](http://research.cofc.edu/administration/index.php). Be sure to include complete publication information \(i.e, a URL, PDF, or PS file of the actual publication\) and indicate if there are any restrictions on publication.

### Grants and Funding

If you are submitting proposals for grant funding with a computational component that can take advantage of our HPC resources, please contact our Research and Grants Administration Office [personnel](http://research.cofc.edu/administration/contact-orga-staff/index.php) and [hpc@cofc.edu](mailto:hpc@cofc.edu) to discuss ways in which

* you can use our HPC resources in your researcher
* the presence of HPC resources can strengthen your proposals
* you can request funding to add to our HPC resources

If your project is supported by grants or other funding, this information should be included on the HPC project website under the grant page \([https://hpc.cofc.edu/projects](https://hpc.cofc.edu/projects)\). This will be used internally to provide a better idea of how CofC researchers are making use of the HPC for externally funded projects.

## Communication Policy

The email account you provided will automatically be subscribed the CofC's HPC mailing list for important system announcements. There will also be a forum and knowledge base platform for users to ask questions and address common problems.

All emails regarding HPC questions, concerns, and maintenance requests should be sent directly to hpc@cofc.edu. Response time will vary depending on the nature of the request and staff workload.

## Policy Violations

If it has been determined that you have violated any of the HPC resource policies, or any other CofC IT policies, your account\(s\) will be deactivated immediately. Your account will not be reactivated until HPC management receives a formal request from your faculty mentor or leader of your project.

If you have any questions or concerns regarding any of these policies, please send an email to [hpc@cofc.edu](mailto:hpc@cofc.edu).

