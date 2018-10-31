# Hardware

## Overall Hardware Configuration

The HPC is a commodity Linux cluster containing many compute, storage and networking equipment all assembled into a standard rack. Please see the rack diagram below for the layout.

|  |   |
|--|---|
| 1  GbE 48-port Switch (4x SPF+ 10GbE ports)	| **internal network** |
| 1 Mellanox 100Gbs 36 port EDR Infiniband Switch	| **interconnect** |
| #7 PowerEdge R740 2x 6-core Intel Xeon-G 6128 3.4GHz CPUs, 192GB RAM, 1x480GB SAS SSDs striped + 1 NVIDIA Tesla V100 GPU	| **1x gpu nodes** |
| #7 PowerEdge R740 2x 6-core Intel Xeon-G 6128 3.4GHz CPUs, 192GB RAM, 1x480GB SAS SSDs striped + 1 NVIDIA Tesla V100 GPU |	**1x gpu nodes** |
| #6 PowerEdge R840 4x 20-core Intel Xeon-G 6148 2.4GHz, 1.5TB RAM, 2x480GB SATA SSD	| **1x large memory node** |
| #5 2U PowerEdge R740 2x 20-core Intel Xeon-G 6148 2.4GHz, 192TB RAM, 1x480GB SATA SSD	| **1x gpu-capable nodes** |
| #5 2U PowerEdge R740 2x 20-core Intel Xeon-G 6148 2.4GHz, 192TB RAM, 1x480GB SATA SSD | **1x gpu-capable nodes** |
| #4 4x PowerEdge C6420 in a 2U chassis 2x 20-core Intel Xeon-G 6148 2.4GHz, 192GB RAM, 1x480GB SSD |	**4x stdmem nodes** |
| #4 4x PowerEdge C6420 in a 2U chassis 2x 20-core Intel Xeon-G 6148 2.4GHz, 192GB RAM, 1x480GB SSD |	**4x stdmem nodes** |
| #3 2U NFS server with NVMe SSDs PowerEdge R740XD 2x Intel Xeon-G 6126 2.6GHz CPU, 192GB RAM,  24x 1.6TB NVMe SSDs |	**fast scratch storage server** |
| #2 2U PowerEdge R740 NFS servers  w/ 2x 12-core Intel Xeon Gold 6136 3.0GHz CPUs, 192GB RAM, 5x300TB 15k SAS HDDs,  |	**NFS servers for long-term storage array**	|
| #2 2U PowerEdge R740 NFS servers w/ 2x 12-core Intel Xeon Gold 6136 CPUs, 192GB RAM, 5x300TB 15k SAS HDDs, |	**NFS servers for long-term storage array**	|
| #2 NSS-HA7 (Dual NFS server) 1x 4U PowerVault MD3460 - RBOD w/ 60x 6TB HDDs | **NSS-HA7 long-term storage array** |
| #1 PowerEdge R740 2x 12-core Intel Xeon-G 6126 2.6GHz CPU, 192GB RAM, 2x480GB SSDs mirrored,  1 NVIDIA Quadro P1000 GPU |	**login/viz node** |

<a href="/using-the-hpc/screenshots/Rack-Diagram.png" ><img src="/using-the-hpc/screenshots/Rack-Diagram.png" alt="Rack Diagram" width="440" border="5" /></a>
<!--
![rack diagram](/using-the-hpc/screenshots/Rack-Diagram.png "rack layout")
-->

---
* [**Compute nodes**](hardware.md)
  * 10 standard compute nodes:
    * Dell PowerEdge R740 or R740XD servers
    * 2x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs w/ 27MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 480GB of local SSD storage,
    * Double precision performance ~ 2.8 TFLOPs/node
  * 1 large memory node:
    * Dell PowerEdge R840 server
    * 4x 20-core 2.4GHz Intel Xeon Gold 6148 CPUs w/ 27MB L3 cache,
    * 1536GB of DDR4 2667MHz RAM,
    * 960GB of local SSD storage,
    * Double precision performance ~ 5.6 TFLOPs/node
  * 2 GPU-containing nodes:
    * Dell PowerEdge R740XD server
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs w/ 19MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 480GB of local SSD storage,
    * 2 NVIDIA Tesla V100 16GB
    * Double precision performance ~ 1.8 + 7.0 = 8.8 TFLOPs/node
* [**Login/visualization node**](hardware.md)
  * 1 login and visualization node:
    * 2x 12-core 2.6GHz Intel Xeon Gold 6126 CPUs w/ 27MB L3 cache,
    * 192GB of DDR4 2667MHz RAM,
    * 480GB of local SSD storage,
    * 1x NVIDIA Quadro P4000 8GB GPU
* [**Storage**](storage.md)
  * 288TB NFS-shared, global, highly-available storage
  * 38TB NFS-shared, global fast scratch storage
* [**Interconnect**](http://www.mellanox.com/page/products_dyn?product_family=192&mtag=sb7700_sb7790)
  * Mellanox EDR Infiniband with 100Gb/s bandwidth

---

## Components

### CPU
|    | Intel Xeon Gold Skylake 6148  |
|----|---|
| **Specs** | [Summary of  specs](https://ark.intel.com/products/123690/Intel-Xeon-Gold-6148F-Processor-27-5M-Cache-2-40-GHz-)|
| **Technical Overview** | [Technical details at Intel including comparison with previous generations](https://software.intel.com/en-us/articles/intel-xeon-processor-scalable-family-technical-overview)|
| **Cores per socket**: | 20 |
| **Clock Speed** | 2.40 GHz base clock, 3.70 GHz Turbo Boost clock |
| **Clock Speed Range** | 2.20 GHz to 3.5GHz depending on instruction set and number of active cores|
| **Hyperthreading** | Possible |
| **Cache Hierarchy** | L1 = 32 KB per core <br> L2= 1 MB per core <br> L3 = 27.5 MB shared per CPU |
| **Configuration** | 2 CPUs per standard or GPU nodes, 4 CPUs per high memory node |
| **Estimated Performance** | 1.4 TeraFLOPS per CPU (double precision) |
| **References** | [1](https://ark.intel.com/products/123690/Intel-Xeon-Gold-6148F-Processor-27-5M-Cache-2-40-GHz-) <br> [2](https://software.intel.com/en-us/articles/intel-xeon-processor-scalable-family-technical-overview) <br> [3](https://en.wikichip.org/wiki/intel/microarchitectures/skylake) <br> [4](https://www.nas.nasa.gov/hecc/support/kb/skylake-processors_550.html) <br>  |

---
### GPU
|  |**NVIDIA Tesla V100**|
|--------------|--------------|
| **Specs** | [Summary of Specs](https://www.nvidia.com/en-us/data-center/tesla-v100/) |
| **Technical Overview** | [Technical details at NVIDIA including comparison w/ previous generations](/using-the-hpc/screenshots/volta-architecture-whitepaper.pdf "") |
| **Architecture** |	Volta
| **GPU** 	| GV100 |
| **CUDA Cores** 	 | 5120 |
| **Tensor Cores** | 	640 |
| **Boost Clock** |		1370MHz |
| **Memory Clock** |	1.75Gbps HBM2 |
| **Memory Bus Width** |	4096-bit HBM2|
| **Memory Bandwidth** |	900GB/sec |
| **Memory Size** |	16GB |
| **L2 Cache** |	6MB |
| **Half Precision** |	28 TFLOPS |
| **Single Precision** |	14 TFLOPS |
| **Double Precision** |	7 TFLOPS 	|
| **Tensor Performance** |		112 TFLOPS |
| **GPU** 	| GV100 |
| **Transistor Count** |	21B |
| **TDP** |	250W |
| **Form Factor** |		PCIe |
| **Cooling** |	Passive |
| **Manufacturing Process** |	TSMC 12nm FFN |
| **Configuration** | 1 GPU per GPU node |
| **Estimated Performance** | 7 TeraFLOPS per GPU (double precision) |
| **References** | [5](https://www.anandtech.com/show/12576/nvidia-bumps-all-tesla-v100-models-to-32gb) <br> [6](https://www.nvidia.com/en-us/data-center/tesla-v100/) <br> [7](http://images.nvidia.com/content/volta-architecture/pdf/volta-architecture-whitepaper.pdf) |

### Interconnect
* Mellanox EDR InfiniBand Interconnect
