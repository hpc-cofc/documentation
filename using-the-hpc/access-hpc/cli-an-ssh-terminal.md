# CLI - an SSH terminal

Most users will access the cluster with a **command line interface \(CLI\) using an SSH client**. However, some may choose a **graphical user interface \(GUI\)** or a **web interface** to use the cluster.

#### Command line interface \(CLI\)

You would need an SSH client on your local computer to connect to the HPC cluster. MacOS and Linux provide SSH clients while most Windows machines require users to install external SSH clients.

In all cases, you would need to provide the following:

* hostname - hpc.cofc.edu
* user name - your user name
* your password or SSH public key location
* protocol and ports -  if not populated by default, you can pick 'SSH' protocol running on port '22'

{% tabs %}
{% tab title="Windows" %}
Windows 10 now has a Bash shell. If you are using an older version of Windows, you have the following options, among others for sure.

* [MobaTerm](https://mobaxterm.mobatek.net) - It provides SSH, X11, VNC and FTP clients .
* [XManager](https://www.netsarang.com/en/xmanager)
* [Git Bash](https://git-scm.com/download/win) – Part of the Git for Windows environment includes Git Bash, which provides a light weight ssh client.
* [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) - SSH client and Bash environment for Windows.
{% endtab %}

{% tab title="MacOS/Linux" %}
Both Mac OS and Linux distributions include a BASH terminal and an SSH client by default. No additional software should be required to access the HPC cluster.

Mac OS users can go to **Applications &gt; Utilities &gt; Terminal.app** to open the Mac Terminal. Different Linux distributions offer terminals and feature them prominently.
{% endtab %}
{% endtabs %}

To log into the cluster, open a terminal and enter the following command:

* `ssh username@hpc.cofc.edu`

If you want the ability to see graphical outputs from the cluster, give `ssh` a '-X' or '-Y' flag.

* `ssh -X username@hpc.cofc.edu`

You will be prompted to enter your password to log in. In the long run, you probably want to generate an SSH key that would allow you to log in without entering a password every time.

