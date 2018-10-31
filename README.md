# About HPC at CofC

High performance computing (HPC) at College of Charleston has historically been under the purview of
the Department of Computer Science. It is now under Division of Information Technology with the aim
of delivering research computing environment and support for the whole campus. 

# Available Resources

We recently purchased a new Linux cluster that will be in full operation in January 2019. In
the meantime, users can feel free to request accounts on our existing cluster via [email](mailto:temelsob@cofc.edu,mosesd@cofc.edu).

The new cluster will be composed of
- 10 compute nodes each with 40 2.4GHz Intel Xeon Skylake cores, 192GB of memory and 480GB of local storage, 
- 1 large memory compute node with 80 2.4GHz  Intel Xeon Skylake cores, 1.5TB of memory and 960GB of local storage,
- 2 GPU-containing nodes each with 24 2.6GHz Intel Xeon Skylake cores, 1 NVIDIA Tesla V100 GPU, 192GB of RAM and 480GB local storage, 
- 1 login and visualization node with 24 2.4GHz Intel Xeon Skylake cores, 1 NVIDIA Quadro P4000 GPU, 192GB of RAM and 480GB local storage, 
- 288TB globally-shared storage, 
- 38TB globally-shared NVMe SSD-based fast scratch storage, 
- all interconnected with EDR Infiniband fabric 

It will run an OpenHPC software stack composed of CentOS 7.5 with Warewulf for management and provisioning, and SLURM as the scheduler. It will 
have all the necessary software libraries and compilers to ensure that users' software compiles and runs optimally on the cluster.

# Making the Best of this Guide

* The **navigation panel** on the left provides you with a birds-eye view of the content of these pages.
* GitBook **search** at the top of the left-hand side allows you to list only content that matches your keywords.

# Support

If you need any help with HPC-related problems, please email [HPC
  support](mailto:temelsob@cofc.edu) directly or via the campus [helpdesk](mailto:helpdesk@cofc.edu)

# Acknowledgements for this Guide

Big thanks to Wendi Sapp (Oak Ridge National Lab/Sustainable Horizons Institute) and the
[CADES](https://cades.ornl.gov/) team at ORNL for allowing this documentation to be shared with the
community.
