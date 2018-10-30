# Overview

## Overview of CofC's HPC Resources

To get started using the HPC, check first to see if you are ready by looking over the [prerequisites](../how-to-use/prerequisites.md). Then, learn how to [request access](../how-to-use/request-access.md). Finally, you are ready to [access your Condo allocation](../how-to-use/access-HPC.md).

### HPC Resources in Brief

* [**Hardware**](hardware.md)
  * 10 standard compute nodes: 
    * 2x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs, 
    * 192GB of DDR4 RAM,
    * 480GB of local SSD storage,
  * 1 large memory node: 
    * 4x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs, 
    * 1536GB of DDR4 RAM, 
    * 960GB of local SSD storage,
  * 2 GPU-containing nodes: 
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs, 
    * 192GB of DDR4 RAM, 
    * 480GB of local SSD storage,
    * 2x NVIDIA Tesla V100 16GB 
  * 1 login and visualization node: 
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs, 
    * 192GB of DDR4 RAM, 
    * 480GB of local SSD storage,
    * 1x NVIDIA Quadro P4000  8GB  GPU
* [**Storage**](storage.md)
  * 288TB NFS-shared, global, highly-available storage
  * 38TB NFS-shared fast scratch storage
* [**Interconnect**](http://www.mellanox.com/page/products_dyn?product_family=192&mtag=sb7700_sb7790)
  * EDR Infiniband w/ 100Gb/s bandwidth
* [**Software stack**](software.md)
  * OpenHPC using CentOS 7.5
  * Warewulf provisioning
  * SLURM scheduler
  * LMod modules for package management
  * Workflow tools

