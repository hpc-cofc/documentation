# Quickstart Guide

One of the biggest challenges for new HPC users is figuring out where to start. This page hopefully
helps overcome that hurdle. If not, you can always email [hpc@cofc.edu](mailto:hpc.cofc.edu) to seek
help.

## Prerequisites

### Request Account

* Faculty and staff can request accounts emailing [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Requesting%20new%20faculty/staff%20account).
* Students are eligible for accounts upon endorsement or sponsorship by their faculty/staff mentor/advisor. Their faculty/staff mentor/advisor can send an email request to [hpc@cofc.edu](mailto:hpc@cofc.edu?subject=Requesting%20new%20student%20account) on their behalf to initiate the account creation process.

You can read more about [requesting account access](request-access.md).

### Software to Access the HPC Cluster

Most users will access the cluster with a command line interface (CLI) using an SSH client. Therefore, you would need an SSH client on your local computer.

### Mac OS and Linux Users

Both Mac OS and Linux distributions include a BASH terminal and an SSH client by default. No additional software should be required to access the HPC cluster.

Mac OS users can go to **Applications > Utilities > Terminal.app** to open the Mac Terminal. Different Linux distributions offer terminals and feature them prominently.

### Windows Users

Windows 10 now has a Bash shell. If you are using an older version of Windows, you have the following options, among others for sure.

* [MobaTerm](https://mobaxterm.mobatek.net) - It provides SSH, X11, VNC and FTP clients .
* [XManager](https://www.netsarang.com/en/xmanager)
* [Git Bash](https://git-scm.com/download/win) – Part of the Git for Windows environment includes Git Bash, which provides a light weight ssh client.
* [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) - SSH client and Bash environment for Windows.

## Logging into the HPC Cluster

To log into the cluster, open a terminal and enter the following command:

**localhost>** `ssh myusername@hpc.cofc.edu`

If you want the ability to see graphical outputs from the cluster, give `ssh` a '-x' or '-y' flag.

**localhost>** `ssh -X myusername@hpc.cofc.edu`

You will be prompted to enter your password to log in. In the long run, you probably want to generate an SSH key that would allow you to log in without entering a password every time.

## Transferring Data to the HPC Cluster

To log into the cluster, open a terminal and enter the following command:

**localhost>** `ssh myusername@hpc.cofc.edu`




The above command will rotate connections across all available login nodes and route your connection to one of them. To connect to a specific login node, use its full domain name:

localhost$ ssh myusername@login2.stampede2.tacc.utexas.edu

To connect with X11 support on Stampede2 (usually required for applications with graphical user interfaces), use the "-X" or "-Y" switch:

localhost$ ssh -X myusername@stampede2.tacc.utexas.edu
Most users will access the cluster with a command line interface (CLI) using an SSH client. Therefore, you would need an SSH client on your local computer.



* [Prerequisites](prerequisites.md)
* [Request Credentials for an Allocation](request-access.md)
* [Access to your Allocation](access-hpc.md)
* [Execute a Job on an Allocation](execute-a-job/)

# Prerequisites

To properly utilize the HPC cluster, you will need a couple of utilities loaded on your local machine. These utilities are free and widely used for this type of application.

* Required: **SSH client**
* Recommended: **Bash terminal**

## MacOS and Linux

Both macOS and Linux distributions include a Bash terminal and an SSH client by default. No additional software should be required to access HPC Condos.

## Windows Users

Windows 10 now has a Bash shell. If you are using an older version of Windows, you have the following options, among others for sure.

* [MobaTerm](https://mobaxterm.mobatek.net) - It provides SSH, X11, VNC and FTP clients .
* [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) - SSH client and Bash environment for Windows.
* [Git Bash](https://git-scm.com/download/win) – Part of the Git for Windows environment includes Git Bash, which provides a light weight ssh client.
