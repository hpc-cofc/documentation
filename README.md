# About HPC at CofC

High performance computing (HPC) at College of Charleston has historically been under the purview of
the Department of Computer Science. It is now under Division of Information Technology with the aim
of delivering research computing environment and support for the whole campus.

# Available Resources

We recently purchased a new Linux cluster that will be in full operation in May 2019.
Faculty and staff can request accounts by emailing [email](mailto:hpc@cofc.edu). Students can ask
their faculty/staff advisors/mentors to submit a request on their behalf.

The new cluster will be composed of
- **10 compute nodes** each with 2x 20-core 2.4GHz Intel Xeon Skylake CPUs, 192GB of memory and 480GB of local storage,
- **1 large memory compute node** with 4x 20-core 2.4GHz  Intel Xeon Skylake CPUs, 1.5TB of memory and 960GB of local storage,
- **2 GPU-containing nodes** each with 2x 12-core 2.6GHz Intel Xeon Skylake CPUs, 1 NVIDIA Tesla V100 GPU, 192GB of RAM and 480GB local storage,
- **1 login and visualization node** with 2x 12-core 24 2.4GHz Intel Xeon Skylake CPUs, 1 NVIDIA Quadro P4000 GPU, 192GB of RAM and 480GB local storage,
- **600TB globally-shared storage**,
- **38TB globally-shared NVMe SSD-based fast scratch storage**,
- **All interconnected with EDR Infiniband fabric**

It will run an **OpenHPC** software stack composed of CentOS 7.5 with Warewulf for management and provisioning, and **SLURM** as the scheduler. It will
have all the necessary **general as well as subject-specific software libraries and compilers** to ensure that users' software compiles and runs optimally on the cluster.

In total, the cluster can do **51 TeraFLOPS** (trillions of floating point operations per second). We will provide benchmarks based on standard High Performance LINPACK (HPL) at some point.

---
# Support and Facilitation

If you need any help, please follow any of the following channels.

- Please email [HPC support](mailto:hpc@cofc.edu) directly or
- Email the campus [helpdesk](mailto:helpdesk@cofc.edu) or
- Call the campus helpdesk at 853-953-3375 during these hours
  - Mon - Fri 7:30 AM - 10:00 PM
  - Sat - Sun 2:00 PM - 10:00 PM
- Submit a support ticket through [TeamDynamix](https://cofc.teamdynamix.com)
- Stop by Bell Building, Room 520 during normal work hours (M-F, 8AM-5PM)

We recognize that there are a lot of hurdles that keep people from using HPC resources. We have experience facilitating research computing for experts and new users alike. So, please feel free to contact us and we will work to get you started.

---
# Acknowledgements for this Guide

Big thanks to Wendi Sapp (Oak Ridge National Lab/[Sustainable Horizons Institute](http://shinstitute.org/wendi-sapp-3/)) and the
[CADES](https://cades.ornl.gov/) team at ORNL for sharing the template for this documentation with the HPC
community.
