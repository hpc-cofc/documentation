# Hardware

## HPC Hardware Configuration

The HPC is a commodity Linux cluster containing many servers/nodes, storage and networking equipment all assembled into a standard rack.

Please see the rack diagram below:

![rack diagram](/using-the-hpc/screenshots/Rack-Diagram.png "rack layout")

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


### CPU Information

* **Specs**: [Full specs](https://ark.intel.com/products/123690/Intel-Xeon-Gold-6148F-Processor-27-5M-Cache-2-40-GHz-)
* **Model**: Intel Xeon Gold Skylake 6148
* **Cores per socket**: 20
* **Clock Speed**: 2.40 GHz base clock, 3.70 GHz Turbo Boost clock
* **Configuration**: 2 CPUs per standard or GPU nodes, 4 CPUs per high memory node

### GPU Information

* **Specs**: [Full Specs](https://www.nvidia.com/en-us/data-center/tesla-v100/)
* **Model**: Tesla K80 \(2 GK210 GPUs on each K80\)
* **Speed**: 560 MHz base clock
* **VRAM**: 24 GB of GDDR5
* **Error correction**: Registered ECC
* **Capacity**: 2 Tesla K80s per node, 2 GK210 GPUs per K80 \(4 total GK210 GPUs per node\)

|  |**NVIDIA Tesla V100**|
|--------------|--------------|
|Architecture |	Volta
| CUDA Cores 	 | 5120 |
| Tensor Cores | 	640 |
| Core Clock  |	? 	|
| Boost Clock |		1370MHz |
| Memory Clock |	1.75Gbps HBM2 |
| Memory Bus Width |	4096-bit |
| Memory Bandwidth |	900GB/sec |
| VRAM |	16GB |
| L2 Cache |	6MB |
| Half Precision |	28 TFLOPS |
| Single Precision |	14 TFLOPS |
| Double Precision |	7 TFLOPS 	|
| Tensor Performance(Deep Learning) |		112 TFLOPS |
| GPU 	| GV100 |
| Transistor Count |	21B |
| TDP |	250W |
| Form Factor |		PCIe |
| Cooling |	Passive |
| Manufacturing Process |	TSMC 12nm FFN |

### Network

* InfiniBand Interconnect
