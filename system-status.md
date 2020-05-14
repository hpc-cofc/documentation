---
description: 'News, updates, outages, maintenance periods'
---

# System News and Updates

## May 2020

#### Updates

* Documentation page moved to [https://docs.hpc.cofc.edu](https://docs.hpc.cofc.edu)
* HPC@CofC highlighted on [Campus IT's biannual newsletter ](https://mailchi.mp/2b6b35b78547/information-technology-newsletter-spring-2020?e=e3ac133ef2#Solving%20the%20Big%20Questions)
* New JupyterHub kernels including Python\[2.7/3.6/3.7\], R, Julia, Matlab, Mathematica, GNUplot, and ArcGIS. ... Check it out at [https://hpc.cofc.edu/jupyterhub](https://hpc.cofc.edu/jupyterhub)
* PGI compilers added

## April 2020

#### Updates 

* JupyterHub installed. Please see the [documentation here](using-the-hpc/scheduling-jobs/jupyterhub.md). Users are encouraged to use it instead of setting up SSH port forwarding themselves.
* FastX3 upgraded to 3.0.46

## March 2020

#### Updates 

* Singularity upgraded to version 3.4.1
* FastX3 upgraded to 3.0.44
* Jave JDK version updated to java/jdk-11.0.7. Use modules to load it.

## February 2020

#### Updates 

* Split view of compute and storage servers in Ganglia 
* New 24-core compute node with 1 NVIDIA Quadro P4000 GPU and 2TB local storage deployed
* [MarvinSuite](https://chemaxon.com/products/marvin) from [ChemAxon](https://chemaxon.com) available on the login node. Some features are not available in the free version, so you may need to get a license by [creating an account](https://accounts.chemaxon.com/register) at ChemAxon and [request a free personal academic license.](https://www.chemaxon.com/my-chemaxon/my-academic-license/)
* Community version of Cambridge Crystallographic Data Centre's [Mercury](https://www.ccdc.cam.ac.uk/Community/csd-community/freemercury/) -- you would need your own license to access features only available in the commercial version such as CSD System, CSD Materials, CSD Discovery

## Dec 2019 - Jan 2020

#### Updates 

* Newly installed software 
  * chem/amber/18-gpu and chem/amber/18-cpu with AmberTools19
  * chem/xtb/6.2.2 
  * math/matlab/r2019b 
  * bio/ncbi-blast+/2.10.0
  * bio/mothur 
* See the example runs [here](https://github.com/hpc-cofc/example-runs)

## November 2019

#### Updates 

* Documentation on our remote desktop service \(StarNet FastX\) is added [here](using-the-hpc/access-hpc/gui-remote-desktop.md). You can download the FastX desktop client or a web client. 
* Documentation on [VisIT](https://visit.llnl.gov) and [ParaView](https://www.paraview.org/) is added [here](using-the-hpc/visualize-data.md). 
* Please run `module spider` to see newly installed and updated software

## October 2019

#### Updates 

* A new remote desktop service \(StarNet FastX\) is available to get a full graphical Linux environment on the HPC. You can download the FastX client for your local computer here. 
* VisIT and ParaView visualizations are now available on the HPC to allow remote visualization of data on the HPC on your local computer. Documentation on these tools will be available soon.
* The Spack package manger is made available to users to compile very complex software stacks in their own space. Please run '`module purge; module load spack`' to set up the Spack environment.

#### Maintenance 

* 10/04/19 - 10/20/19 : network access to the HPC may be blocked from certain locations during some traffic rerouting attempts to optimize the network's throughput

## September 2019

#### Updates 

* A host of new bioinformatics packages are now installed on the cluster. You can access them using modules from a common area or install the Bioconda package from Anaconda to install them in your home directory. These packages are 
  * bio/vcftools, bio/samtools, bio/ngstools, bio/minimap2, bio/hisat2, bio/bwa, bio/bowtie2, bio/bowtie, bio/bedtools, bio/angsd 
  * see [examples at CofC-HPC GitHub page](https://github.com/hpc-cofc/example-runs/tree/master/10_bio)
* For other newly installed software, please run `module spider`. There should be accompanying example runs at [CofC-HPC GitHub page](https://github.com/hpc-cofc/example-runs/tree/master/10_bio)
* More documentation including YouTube videos are in the works. Please check in later for links

## August 2019

#### Updates 

* Standard version of [AIMALL](http://aim.tkgristmill.com/) is installed to do atoms-in-molecules\(AIM\) analysis on molecular systems starting from quantum mechanical wavefunctions.
* The host name of the login node \(hpc.cofc.edu\) has been aliased as 'openhpc.cofc.edu'
* Documentation on using a Cendio Thinlinc client to get remote desktop access to the cluster is added [here](https://hpc-cofc.gitbook.io/docs/using-the-hpc/quickstart#graphical-user-interface-gui).

#### Maintenance

* A maintenance period will be scheduled at the end of the month to enable database integration to our scheduler and make other changes. 

## July 2019

#### Updates

* Jupyter Notebooks are now available. You can set up your own Anaconda environment to run Python2/3, R and other codes using a web Jupyter Notebook. Please see the [Jupyter Notebooks](using-the-hpc/scheduling-jobs/jupyter-notebooks.md) page 

#### Maintenance

* Network access to the cluster will be intermittent Thursday, July 18, 2019 from 1:30PM to 4:00PM due to a planned firewall upgrade in the datacenter. All your calculations and services that are not dependent on external network access will proceed uninterrupted. Please report any problems to [hpc@cofc.edu](mailto:hpc@cofc.edu).

## June 2019

#### Updates

* The available software has been expanded substantially. Please check the [Software List](using-the-hpc/modules/software.md) or enter `module spider` to see the current list. 

#### Maintenance

* 05/20/19-07/03/19 - Support will be limited due to staff vacations. We will try to accommodate any requests sent to [hpc@cofc.edu](mailto:hpc@cofc.edu).

## May 2019

#### Updates

* R/3.4.2 and R/3.5.2 are added for the GNU7/8-openmpi3 and Intel-openmpi3 stacks
* The available software has been expanded substantially. Please check the Software List or enter `module spider` to see the current list.

#### Outage

* 05/20/19 - a cooling problem in our campus datacenter forced us to power down the cluster for 10 hours. Everything has been restored to its normal state. Please report any problems to [hpc@cofc.edu](mailto:hpc@cofc.edu).

## April 2019

#### Updates

* 04/25/19 - WebMO installation is up with interfaces to many computational chemistry software including Gaussian16, GAMESS, Orca, Psi4 and MOPAC
* 04/22/19 - the cluster is open to all campus users. Please feel free to [Request an Account](using-the-hpc/request-access.md)
* 04/05/19 - the cluster is open to a few users for testing. It'll be open to all other users in two weeks if it is deemed ready for production runs. 

## March 2019

#### Updates

* 03/07/19 - The HPC cluster is installed by Dell-EMC.
* 03/11/19 - Testing and benchmarking the cluster
* 03/26/19 - HPC software stack installation
* 04/02/19 - Configuration of user environments
* 04/05/19 - Cluster open to a few test users 
* 04/22/19 - Cluster open to all users.





