# WebMO

[WebMO](https://www.webmo.net) is a web interface to many computational chemistry programs. It has many powerful capabilities
that give users access to computational chemistry tools without having to use a command line.

## Capabilities
### Visualization
[WebMO Enterprise](https://www.webmo.net/enterprise/index.html) has the following
capabilites:
- Build molecules by drawing atoms and bonds in a 3-D molecular editor, or by speaking the name (e.g., “aspirin”)
- Optimize structures using VSEPR theory or molecular mechanics
- View Huckel molecular orbitals, electron density, and electrostatic potential
- View point group and symmetry elements of molecules
- Lookup basic molecular information, including IUPAC and common names, stoichiometry, molar mass
- Lookup chemical data from PubChem and ChemSpider
- Lookup experimental and predicted molecular properties from external databases (NIST, Sigma-Aldrich)
- Lookup IR, UV-VIS, NMR, and mass spectra from external databases (NIST, NMRShiftDB)

### Interfaces to Common Packages
Our WebMO installation provides interfaces to the following packages:
- Gaussian,
- GAMESS,
- ORCA
- MOPAC
- PSI
- Molpro
- NWChem
- PQS
- Quantum Espresso
- VASP
- Q-Chem
- Tinker

### Integration to Queue Manager
- Submit, monitor, and view calculations
- View formatted tabular data extracted from output files, as well as raw output
- Visualize geometry, partial charges, dipole moment, normal vibrational modes, molecular orbitals, and NMR/IR/UV-VIS spectra

---
## Notes about using the CofC WebMO Installation

We have a WebMO Enterprise installation at [https://hpc.cofc.edu/webmo](https://hpc.cofc.edu/webmo).
To request an account, please
- email [hpc@cofc.edu](mailto:hpc@cofc.edu) OR
- submit a [service request](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085).

### Best Way to Learn about WebMO

WebMO has a very user-friendly interface. The quickest way to learn about it is to go over these YouTube tutorials

- [WebMO basics (7:30)](https://www.youtube.com/watch?v=X_JbEtytasE)
- [Computational Chemistry using WebMO at UoA (26:12)](https://www.youtube.com/watch?v=iZqYmd10mgg)

Below are notes about using our WebMO installation safely and effectively.

### Hardware
WebMO calculations are run on compute nodes with the following raw specs:
- **10 stdmem nodes** each with 2x 20-core 2.4GHz Intel Xeon Skylake CPUs, 192GB of RAM and 480GB of raw local storage,
- **1 bigmem node** with 4x 20-core 2.4GHz  Intel Xeon Skylake CPUs, 1536GB of RAM and 960GB of raw local storage,

In short, these two compute node types provide the following resources
- **10 stdmem nodes** each with 40 cores, 192GB of RAM (4.8GB/core) and 300GB local scratch storage
- **1 bigmem node** with 80 cores, 1536GB of RAM (19.2GB/core) and 660GB of local scratch storage,

These specs should guide what resources you request to run your calculations.

### Queues
There are two queues that you can submit your WebMO calculations to. Please choose the appropriate queue based on your needs. If you are unsure, the **stdmemq** should be able to meet most of your needs.
- **stdmemq** - Most calculations should be sent to queue. It has a 24-hour run limit. Anything submitted to this queue runs on the **stdmem** nodes.
- **debugq** - this queue is intended for short calculations running for 60 minutes or less. Anything submitted to this queue runs on the **stdmem** nodes.
- **bigmemq** - this queue is intended for calculations requiring lots of memory (4.8 - 19.2 GB/core) or local scratch storage.

Queue  | Time limit (hrs) | #CPU limit | Memory limit(GB) | Scratch disk limit (GB) |Best use
------ |-------------| ----------- | ------ | --------
debugq | 1 | 40 | 4.8/core | 300 | Quick test calculations lasting less than 1 hr
stdmemq | 24 | 40 | 4.8/core | 300 | Most typical calculations
bigmemq | 24 | 40 | 19.2/core | 600 | Calculations needing lots of memory

### Interfaces
Our WebMO installation provides interfaces to the following packages:
- Gaussian,
- GAMESS,
- ORCA
- MOPAC
- PSI

In the future, we will provide interface to these following packages based on the level of interest
and availability of the licenses for the packages.
- Molpro, NWChem, PQS, Quantum Espresso, VASP, Q-Chem, and Tinker

Please see the following tips to run your calculations optimally.

#### Gaussian
- See [Gaussian's support page](http://gaussian.com/techsupport) to learn about its capabilities.
- Please note that we do not have license for Linda to run calculations across multiple nodes. So, all your calculations would need to run within a single node.
- Depending the size of your molecule, the method and basis set you are using, and the type of calculation you are running, Gaussian's parallel efficiency varies. In general, it scales well up to 16 compute cores. Therefore, you should use up to 16 cores even though the default number of compute cores is set to 8. In the 'Preview' tab before submitting your calculation, you can make sure the first line of your input file shows `%NProcShared=16` or `%NProcShared=8`
- All our compute nodes have 4.8 GB/core, except for big memory node which has 19.2GB/core. Therefore, you should request about 4GB/core for your calculation. For example, you can add the line `%MEM=32GB` right below `%NProcShared=8` and `%MEM=64GB` before `%NProcShared=16`. In short, If you are requesting `N` cores via `%NProcShared=N`, you should request `%MEM=(N*4)GB`.
- You should try to run MP2, MP4, CCSD, CCSD(T) calculations in integral direct mode as much as possible to prevent substantial slowdown that comes from writing lots of data to disk.

#### GAMESS
- See [GAMESS's site](https://www.msg.chem.iastate.edu/gamess/)
- GAMESS scales well within a node. We encourage you to use 8-16 cores in general, but you can request as many as 40 cores if necessary.
- GAMESS's default memory is too low and that will cause most sizeable calculations to fail due to lack of memory. Therefore, you would need to set the memory to a more reasonable number.
  - In the `Advanced` tab, enter `500` or a larger number for the `Memory` field. That sets the memory per process to 500 megawords or 500 * 8 = 4GB.

#### ORCA
- See [ORCA's forum](https://orcaforum.kofo.mpg.de) to learn more and seek help
- A good summary of its capabilities is available at the [ORCA Input Library](https://sites.google.com/site/orcainputlibrary/home)
- ORCA is a fantastic package with lots of capabilities. It scales very well within a node and has reasonable default settings. We encourage you to use 8-16 cores in general, but you can request as many as 40 cores if necessary.

#### MOPAC
- See [MOPAC's site](http://openmopac.net) to learn more about its capabilies
- MOPAC provides access to quick semiempirical methods for calculations on molecules of any size quickly. By default, it will use 1 core and a limited amount of memory.

### Caveats
- If your calculation needs more than 600GB of scratch storage, please contact [hpc@cofc.edu](mailto:hpc@cofc.edu) about using the HPC's global scratch storage.
