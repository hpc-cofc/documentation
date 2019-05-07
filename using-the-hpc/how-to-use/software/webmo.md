# WebMO

[WebMO](https://www.webmo.net) is a web interface to many computational chemistry programs. It has many powerful capabilities
that give users access to computational chemistry tools without having to use a command line.

We have a WebMO Enterprise installation at [https://hpc.cofc.edu/webmo](https://hpc.cofc.edu/webmo).
To request an account, please
- email [hpc@cofc.edu](mailto:hpc@cofc.edu) OR
- submit a [service request](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=35085).

## Capabilities
### Visualization
Our [WebMO Enterprise](https://www.webmo.net/enterprise/index.html) installation has the following
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

In the future, we will provide interface to these following packages based on the level of interest
and availability of the licenses for the packages.
- Molpro, NWChem, PQS, Quantum Espresso, VASP, Q-Chem, and Tinker

### Integration to Queue Manager
- Submit, monitor, and view calculations
- View formatted tabular data extracted from output files, as well as raw output
- Visualize geometry, partial charges, dipole moment, normal vibrational modes, molecular orbitals, and NMR/IR/UV-VIS spectra

---
## Notes about using WebMO
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

Queue  | Time limit (hrs) | #CPU limit | Memory limit (GB) | Scratch limit (GB) |Best use
------ |-------------| ----------- | ------ | --------
debugq | 1 | 40 | 4.8 | 300GB | Quick test calculations lasting less than 1 hr
stdmemq | 24 | 40 | 4.8 | 300GB | Most typical calculations
bigmemq | 24 | 40 | 19.2 | 600GB | Calculations needing lots of memory

### Interfaces
Our WebMO installation provides interfaces to the following packages:

#### Gaussian
- Gaussian
  - Gaussian jobs scale well up to 16 compute cores. Therefore, you should use up to 16 cores even though the default number of compute cores The dewithin a comp
- GAMESS,
- ORCA
- MOPAC
- PSI

### Interfaces
Our WebMO installation provides interfaces to the following packages:
- Gaussian
  -
- GAMESS,
- ORCA
- MOPAC
- PSI

### Caveats
- If your calculation needs more than 600GB of scratch storage, please contact [hpc@cofc.edu](mailto:hpc@cofc.edu) about using the HPC's global scratch storage.
