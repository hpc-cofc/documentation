# About HPC at CofC

High performance computing (HPC) at College of Charleston has historically been under the purview of
the Department of Computer Science. It is now under the Division of Information Technology with the aim
of delivering a research computing environment and support for the whole campus. We especially thank the following groups for making HPC at CofC possible.
* [Office of the President](http://president.cofc.edu/about/index.php)
* [Division of Information Technology](http://it.cofc.edu)
* [School of Sciences and Mathematics](http://ssm.cofc.edu)

# Available Resources

We recently purchased a new Linux cluster that will be in full operation in late April 2019.
Faculty and staff can request accounts by emailing [hpc@cofc.edu](mailto:hpc@cofc.edu) or filling out a [service request](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085). Students are eligible for accounts upon endorsement or sponsorship by their faculty/staff mentor.

The new cluster is composed of
- **10 compute nodes** each with 2x 20-core 2.4GHz Intel Xeon Skylake CPUs, 192GB of memory and 480GB of local storage,
- **1 large memory compute node** with 4x 20-core 2.4GHz  Intel Xeon Skylake CPUs, 1.5TB of memory and 960GB of local storage,
- **2 GPU-containing nodes** each with 2x 12-core 2.6GHz Intel Xeon Skylake CPUs, 1 NVIDIA Tesla V100 GPU, 192GB of RAM and 480GB local storage,
- **1 login and visualization node** with 2x 12-core 24 2.4GHz Intel Xeon Skylake CPUs, 1 NVIDIA Quadro P4000 GPU, 192GB of RAM and 480GB local storage,
- **512TB globally-shared storage**,
- **38TB globally-shared NVMe SSD-based fast scratch storage**,
- **All interconnected with 100Gbps Mellanox EDR InfiniBand fabric**

It runs an **OpenHPC** software stack composed of CentOS 7.6 with WareWulf for management and provisioning, and **SLURM** as the scheduler. It has all the necessary **general as well as subject-specific software libraries and compilers** to ensure that users' software compiles and runs optimally on the cluster.

In total, the cluster can do **51 TeraFLOPS** (trillions of floating point operations per second). We will provide benchmarks based on standard High Performance LINPACK (HPL) at some point.

---
# Support and Facilitation

If you need any help, please follow any of the following channels.

- Submit a support ticket through [TeamDynamix](https://cofc.teamdynamix.com)
  - [Service requests](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085). These include inquiries about accounts, projects and services
    - Request account
    - Seek consultation about teaching/research projects
    - Inquire about operations
    - Ask about documentation
  - [Incident requests](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35086). These include any problems you encounter during any HPC operations
    - Inability to access the cluster or individual nodes
    - Inability to run calculations
    - Inability to access data
- If TeamDynamix is inacessible, please email [HPC support](mailto:hpc@cofc.edu) directly or
- Email the campus [helpdesk](mailto:helpdesk@cofc.edu) or
- Call the campus helpdesk at 853-953-3375 during these hours
  - Mon - Fri 7:30 AM - 10:00 PM
  - Sat - Sun 2:00 PM - 10:00 PM
- Submit a support ticket through [TeamDynamix](https://cofc.teamdynamix.com)
- Stop by Bell Building, Room 520 during normal work hours (M-F, 8AM-5PM)

We recognize that there are a lot of hurdles that keep people from using HPC resources. We have experience facilitating research computing for experts and new users alike. So, please feel free to contact us and we will work to get you started.

---
# Acknowledgements for this Guide

Big thanks to Wendi Sapp (Oak Ridge National Lab (ORNL) [CADES](https://cades.ornl.gov/), [Sustainable Horizons Institute](http://shinstitute.org/wendi-sapp-3/), [USD Research Computing Group]( http://rcg.usd.edu)) and the team at ORNL for sharing the template for this documentation with the HPC community. You can find Wendi's original documentation on [GitHub](https://github.com/wendikristine/documentation-template)
