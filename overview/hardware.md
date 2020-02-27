# Hardware

## SUMMARY

The cluster has 13 compute nodes including 2 GPU nodes, a login node,  a high-availability storage server connected to a 512TB disk array and a fast scratch server with 40TB of storage. It's accessible to the CofC campus via a 10Gbps ethernet link. The specs are summarized below.

* [**Compute nodes**](hardware.md)
  * 10 standard compute nodes:
    * Dell PowerEdge servers
    * 2x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs w/ 27MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 480GB of local SSD storage,
    * Double precision performance ~ 2.8 TFLOPs/node
  * 1 large memory node:
    * Dell PowerEdge server
    * 4x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs w/ 27MB L3 cache,
    * 1536GB of DDR4 2667MHz RAM,
    * 960GB of local SSD storage,
    * Double precision performance ~ 5.6 TFLOPs/node
  * 3 GPU-containing nodes:
    * Dell PowerEdge server
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs w/ 19MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 480GB of local SSD storage,
    * GPUs
      * the first two have 1 NVIDIA Tesla V100 16GB GPU each
      * the third has 1 NVIDIA Pascal Quadro P4000 8GB GPU
    * Double precision performance 
      * those with 1 NVIDIA Tesla V100 16GB GPU ~ 1.8 + 7.0 = 8.8 TFLOPs/node
      * those with 1 NVIDIA Pascal Quadro P4000 8GB GPU ~ 1.8 + 2.6 = 4.4 TFLOPs/node
* [**Login/visualization node**](hardware.md)
  * 1 login and visualization node:
    * Dell PowerEdge server
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs w/ 27MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 960GB of local SSD storage,
    * 3TB RAID5 storage
    * 1x NVIDIA Quadro P4000 8GB GPU
* [**Storage**](storage.md)
  * 512TB NFS-shared, global, highly-available storage
  * 38TB NFS-shared, global fast scratch storage
* [**Interconnect**](http://www.mellanox.com/page/products_dyn?product_family=192&mtag=sb7700_sb7790)
  * Mellanox EDR Infiniband with 100Gb/s bandwidth

## Hardware Specs

The HPC cluster is a commodity Linux cluster containing many compute, storage and networking equipment all assembled into a standard rack. Please see the table below or the rack diagram further down for the layout.

| Component Specs | Component |
| :--- | :--- |
| 1  GbE 48-port Switch \(4x SPF+ 10GbE ports\) | **internal network** |
| 1 Mellanox 100Gbs 36-port EDR Infiniband Switch | **interconnect** |
| \#8 PowerEdge R740 2x 12-core Intel Xeon-G 6128 3.4GHz CPUs, 192GB RAM, 1x480GB SAS SSDs striped + 1 NVIDIA Quadro P4000 GPU | **1x p4000 gpu node** |
| \#7 PowerEdge R740 2x 12-core Intel Xeon-G 6128 3.4GHz CPUs, 192GB RAM, 1x480GB SAS SSDs striped + 1 NVIDIA Tesla V100 GPU | **1x v100 gpu node** |
| \#7 PowerEdge R740 2x 12-core Intel Xeon-G 6128 3.4GHz CPUs, 192GB RAM, 1x480GB SAS SSDs striped + 1 NVIDIA Tesla V100 GPU | **1x v100 gpu node** |
| \#6 PowerEdge R840 4x 20-core Intel Xeon-G 6148 2.4GHz, 1.5TB RAM, 2x480GB SATA SSD | **1x large memory node** |
| \#5 2U PowerEdge R740 2x 20-core Intel Xeon-G 6148 2.4GHz, 192TB RAM, 1x480GB SATA SSD | **1x gpu-capable node** |
| \#5 2U PowerEdge R740 2x 20-core Intel Xeon-G 6148 2.4GHz, 192GB RAM, 1x480GB SATA SSD | **1x gpu-capable node** |
| \#4 4x PowerEdge C6420 in a 2U chassis 2x 20-core Intel Xeon-G 6148 2.4GHz, 192GB RAM, 1x480GB SSD | **4x stdmem nodes** |
| \#4 4x PowerEdge C6420 in a 2U chassis 2x 20-core Intel Xeon-G 6148 2.4GHz, 192GB RAM, 1x480GB SSD | **4x stdmem nodes** |
| \#3 2U NFS server with NVMe SSDs PowerEdge R740XD 2x Intel Xeon-G 6126 2.6GHz CPU, 192GB RAM,  24x 1.6TB NVMe SSDs | **fast scratch storage server** |
| \#2 2U PowerEdge R740 NFS servers  w/ 2x 12-core Intel Xeon Gold 6136 3.0GHz CPUs, 192GB RAM, 5x300TB 15k SAS HDDs, | **NFS servers for long-term storage array** |
| \#2 2U PowerEdge R740 NFS servers w/ 2x 12-core Intel Xeon Gold 6136 CPUs, 192GB RAM, 5x300TB 15k SAS HDDs, | **NFS servers for long-term storage array** |
| \#2 NSS-HA7 \(Dual NFS server\) 1x 5U  Dell EMC PowerVault ME4084 - RBOD w/ 84x 8TB HDDs | **NSS-HA7 long-term storage array** |
| \#1 PowerEdge R740 2x 12-core Intel Xeon-G 6126 2.6GHz CPU, 192GB RAM, 2x480GB SSDs mirrored,  1 NVIDIA Quadro P1000 GPU | **login/viz node** |

## Layout

![rack layout](../.gitbook/assets/rack-diagram.png)



## Components

### CPU

|  | Intel Xeon Gold Skylake 6148 |
| :--- | :--- |
| **Specs** | [Summary of  specs](https://ark.intel.com/products/123690/Intel-Xeon-Gold-6148F-Processor-27-5M-Cache-2-40-GHz-) |
| **Technical Overview** | [Technical details at Intel including comparison with previous generations](https://software.intel.com/en-us/articles/intel-xeon-processor-scalable-family-technical-overview) |
| **Cores per socket**: | 20 |
| **Clock Speed** | 2.40 GHz base clock, 3.70 GHz Turbo Boost clock |
| **Clock Speed Range** | 2.20 GHz to 3.5GHz depending on instruction set and number of active cores |
| **Hyperthreading** | Possible |
| **Cache Hierarchy** | L1 = 32 KB per core   L2= 1 MB per core   L3 = 27.5 MB shared per CPU |
| **Configuration** | 2 CPUs per standard or GPU nodes, 4 CPUs per high memory node |
| **Estimated Performance** | 1.4 TeraFLOPS per CPU \(double precision\) |
| **References** | [1](https://ark.intel.com/products/123690/Intel-Xeon-Gold-6148F-Processor-27-5M-Cache-2-40-GHz-) ,  [2](https://software.intel.com/en-us/articles/intel-xeon-processor-scalable-family-technical-overview), [3](https://en.wikichip.org/wiki/intel/microarchitectures/skylake),  [4](https://www.nas.nasa.gov/hecc/support/kb/skylake-processors_550.html) |

### GPU

|  | **NVIDIA Tesla V100** |
| :--- | :--- |
| **Specs** | [Summary of Specs](https://www.nvidia.com/en-us/data-center/tesla-v100/) |
| **Technical Overview** | [Technical details at NVIDIA including comparison w/ previous generations](https://github.com/hpc-cofc/documentation/tree/b8d627c8e15312d4f9047674afd89fd5590c62cc/using-the-hpc/screenshots/volta-architecture-whitepaper.pdf) |
| **Architecture** | Volta |
| **GPU** | GV100 |
| **CUDA Cores** | 5120 |
| **Tensor Cores** | 640 |
| **Boost Clock** | 1370MHz |
| **Memory Clock** | 1.75Gbps HBM2 |
| **Memory Bus Width** | 4096-bit HBM2 |
| **Memory Bandwidth** | 900GB/sec |
| **Memory Size** | 16GB |
| **L2 Cache** | 6MB |
| **Half Precision** | 28 TFLOPS |
| **Single Precision** | 14 TFLOPS |
| **Double Precision** | 7 TFLOPS |
| **Tensor Performance** | 112 TFLOPS |
| **GPU** | GV100 |
| **Transistor Count** | 21B |
| **TDP** | 250W |
| **Form Factor** | PCIe |
| **Cooling** | Passive |
| **Manufacturing Process** | TSMC 12nm FFN |
| **Configuration** | 1 GPU per GPU node |
| **Estimated Performance** | 7 TeraFLOPS per GPU \(double precision\) |
| **References** | [5](https://www.anandtech.com/show/12576/nvidia-bumps-all-tesla-v100-models-to-32gb),  [6](https://www.nvidia.com/en-us/data-center/tesla-v100/), [7](http://images.nvidia.com/content/volta-architecture/pdf/volta-architecture-whitepaper.pdf) |

### Interconnect

* Mellanox EDR \(100 Gbps\) InfiniBand interconnect
* 1:1 non-blocking

### Storage

* Long-term HDD-based NFS $HOME storage -  highly redundant and resilient.
  * 512 TB in total
  * Will eventually be backed up weekly, but not yet
  * Peak performance - 7 GBps / 6 GBps for sequential read/write
* Short-term NVMe SSD-based NFS $SCRATCH storage -  fast storage for intermediate data during the course of a computation
  * 38 TB in total
  * Never backed up; purged weekly or as needed
  * Theoretical peak performance ~ 28 GBps / 28 GBps for sequential read/write
  * Expected peak performance ~ 12 GBps / 12 GBps for sequential read/write
  * Actual peak performance -  8 GBps / 5 GBps for sequential read/write

