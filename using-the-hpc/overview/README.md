# Overview

## Overview of CofC's HPC Resources

The specs for the cluster are provided below.
<!--
To get started using the HPC, check first to see if you are ready by looking over the
[prerequisites](../how-to-use/prerequisites.md). Then, learn how to [request
access](../how-to-use/request-access.md). Finally, you are ready to [access your Condo
allocation](../how-to-use/access-HPC.md).
-->

### HPC Cluster Specs in Brief

* [**Compute nodes**](hardware.md)
  * 10 standard compute nodes:
    * 2x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs w/ 27MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 1x 480GB of local SSD storage,
    * Double precision performance ~ 2.8 TFLOPs/node
  * 1 large memory node:
    * 4x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs w/ 27MB L3 cache,
    * 1536GB of DDR4 2667MHz RAM,
    * 2x 480GB of local SSD storage,
    * Double precision performance ~ 5.6 TFLOPs/node
  * 2 GPU-containing nodes:
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs w/ 19MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 480GB of local SSD storage,
    * 1 NVIDIA Tesla V100 16GB GPU
    * Double precision performance ~ 1.8 + 7.0 = 8.8 TFLOPs/node
* [**Login/visualization node**](hardware.md)
  * 1 login and visualization node:
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs w/ 27MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 3TB of local apps storage,
    * 1x NVIDIA Quadro P4000 8GB GPU
* [**Storage**](storage.md)
  * 512TB NFS-shared, global, highly-available storage
  * 38TB NFS-shared, global fast NVMe-SSD-based scratch storage
* [**Interconnect**](http://www.mellanox.com/page/products_dyn?product_family=192&mtag=sb7700_sb7790)
  * Mellanox EDR Infiniband with 100Gb/s bandwidth
* [**Software stack**](software.md)
  * OpenHPC 1.3.6
  * CentOS 7.6
  * Warewulf provisioning
  * SLURM scheduler
  * LMod modules for package management
  * Workflow tools

In total, the cluster has a theoretical peak performance of 51 trillion floating point operations per second (TeraFLOPS). We will provide benchmarks based on standard High Performance LINPACK (HPL) at some point.
