# Access Your HPC Allocation

## On-campus Access
The CofC HPC cluster is accessible directly via SSH from the CofC campus wired and 'eduroam' wireless network.

## Off-campus Access
If you are off-campus, you would need to use CofC's VPN to access the HPC resource. If you have never used CofC's HPC resources before, you would need to submit a VPN access request even if you have used CofC's VPN to access other campus resources.

The process to request VPN access is:

1. Go to the [TeamDynamix VPN Access Request (Pulse VPN)](https://cofc.teamdynamix.com/TDClient/Requests/ServiceDet?ID=13575) page

2. Click on the 'Request VPN Access' button on the right

3. For **Request Type**, select `new` if this is your first time requesting VPN access, or `add` if you just need to be added to the HPC access group

4. For **Request and Justification**, enter
  * `Server Name:` hpc.cofc.edu (153.9.128.11)
  * `Justification:` Description of how you intend to use the HPC cluster

It's identity management group will try to add you to the HPC access list and get you on your way quickly, but expect some delays depending on their workload.

## Once You are Given Access
After your [access request](request-access.md) has been approved and you have installed the [prerequisites](prerequisites.md)

1. Open a Bash terminal (or see [here](prerequisites.md) if you need more help).

2. Execute `ssh username@hostname`.

3. When prompted, enter your password.

**By default, `/home/$USER`, `/globalscratch/$USER` and `/localscratch/$USER` directories should be automatically created when you log into the HPC if they aren't created already.**.

You can run the following command on your terminal to see your files:

```bash
$ ls -lhtr /home/username
total 20K
drwxr-xr-x 2 username groupname 4     Apr 6 12:11 Test1
-rw-r--r-- 1 username groupname 982   Apr 6 12:11 setup.py
-rw-r--r-- 1 username groupname 1.5K  Apr 6 12:11 readme.txt
-rw-r--r-- 1 username groupname 77    Apr 6 12:11 paralleltestpy2.py
```

- The `ls -lhtr /home/username` command will show the whole list and details of the files that the **username** has.
