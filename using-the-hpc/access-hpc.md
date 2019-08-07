# Access your Account

## On-campus Access

The CofC HPC cluster is accessible directly via SSH from the CofC campus wired and 'eduroam' wireless network.

## Off-campus Access

[Remote access](http://it.cofc.edu/network/remote) to the cluster from outside the CofC campus network requires the use of VPN much like access to other campus resources. If you are off-campus, you would need to use CofC's VPN to access the HPC resource. If you have never used CofC's HPC resources before, you would need to submit a VPN access request even if you have used CofC's VPN to access other campus resources.

The process to request VPN access is:

1. Go to the [TeamDynamix VPN Access Request \(Pulse VPN\)](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=13575) page
2. Click on the 'Request VPN Access' button on the right
3. For **Request Type**, select `new` if this is your first time requesting VPN access, or `add` if you just need to be added to the HPC access group
4. For **Request and Justification**, enter
   * `Server Name:` hpc.cofc.edu \(153.9.128.11\)
   * `Justification:` Description of how you intend to use the HPC cluster

Our identity management group will try to add you to the HPC access list and get you on your way quickly, but expect some delays depending on their workload.

## Once You are Given Access

After your [access request](request-access.md) has been approved, your account will be created and you will be sent your access credentials and preliminary information to get you started.

1. Open terminal or SSH client
   * **On Macs and Linux and Windows 10** - Open a terminal \(Terminal, xterm, iTerm, Windows Terminal ... \)
   * **On Windows using SSH Clients** - Open SSH clients such as
     * [MobaTerm](https://mobaxterm.mobatek.net)
     * [XManager](https://www.netsarang.com/en/xmanager)
     * [Git Bash](https://git-scm.com/download/win)
     * [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
2. Connect to the cluster
   * **On Macs and Linux and Windows 10**
     * Execute `ssh username@hpc.cofc.edu`.
   * **On Windows using SSH Clients** - fill in the following information
     * protocol - `SSH`
     * port number - `22`
     * host or hostname - `hpc.cofc.edu`
     * login or username - your HPC user name
     * password - your HPC password  \(you can set up authentication using SSH keys later\).
     * Accept prompt warning if this is the first time you are connecting the HPC
3. Once you have logged in to the HPC, the first thing you want to do is change your password by entering the `passwd` command

```sql
username@hpc[~] passwd
Changing password for user username.
Changing password for username.
(current) UNIX password:
New password:
New password:

Password successully changed.
```

[![asciicast](https://asciinema.org/a/250343.svg)](https://asciinema.org/a/250343?t=4)

1. By default, `/home/$USER`, `/globalscratch/$USER` and `/scratch/$USER` directories should be

   automatically created when you log into the HPC if they aren't created already. Also, a

   `slurm_examples` directory provides simple examples of SLURM submission files. There will also be

   other test directories from software you expressed interest in in your account request form.

You can run the following command on your terminal to see your files:

```sql
username@hpc[~] ls -lhtr /home/username
total 20K
drwxr-xr-x 2 username groupname 4     Apr 6 12:11 00_slurm-examples
-rw-r--r-- 1 username groupname 982   Apr 6 12:11 sample.slurm
-rw-r--r-- 1 username groupname 1.5K  Apr 6 12:11 11_AMBER
```

The `ls -lhtr /home/username` command will show the whole list and details of the files that the **username** has.

