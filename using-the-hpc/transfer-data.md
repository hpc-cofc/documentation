# Transfer Data

CofC's HPC's 10Gbps ethernet connection to the rest of the campus and outside networks allow for fast movement of large data sets into and out of the cluster. There are several transfer tool/protocol options to choose from to fit your needs.

## Using the Command Line

Commandline \(CLI\) tools like `scp`, `rsync` and `sftp` are quick ways to move data around within a computer or among computers. In all the examples below, the `local_host` and `remote_host` is either the IP address or fully qualified domain name \(FQDN\) of the hosts. For example, if you are transferring data from your desktop to the HPC cluster, `local_host` would be `mydesktop.cougars.int` and `remote_host` would be `hpc.cofc.edu`.

### scp

Secure Copy Protocol \(`scp`\) is a commandline tool that allows you to copy files between hosts securely over SSH.using Secure Copy Protocol over SSH.

In fact, [TLDR](https://tldr.sh/) provides a quick summary of the ways in which you can use `scp` to transfer data.

* Copy a local file to a remote host:

  `scp path/to/local_file remote_host:path/to/remote_file`

* Copy a file from a remote host to a local directory:

  `scp remote_host:path/to/remote_file path/to/local_directory`

* Recursively copy the contents of a directory from a remote host to a local directory:

  `scp -r remote_host:path/to/remote_directory path/to/local_directory`

* Copy a file between two remote hosts transferring through the local host:

  `scp -3 host1:path/to/remote_file host2:path/to/remote_directory`

* Use a specific username when connecting to the remote host:

  `scp path/to/local_file remote_username@remote_host:path/to/remote_directory`

* Use a specific ssh private key for authentication with the remote host:

  `scp -i ~/.ssh/private_key local_file remote_host:/path/remote_file`

### rsync

[rsync](https://rsync.samba.org/) allows copying or syncing of data within a single host or between a local and remote host securely over SSH. It is powerful both in terms of its speed and capabilities.

[TLDR](https://tldr.sh/) provides the following usage examples:

* Transfer file from local to remote host:

  `rsync path/to/file remote_host_name:remote_host_location`

* Transfer file from remote host to local:

  `rsync remote_host_name:remote_file_location local_file_location`

* Transfer file in archive \(to preserve attributes\) and compressed \(zipped\) mode with verbose and human-readable progress:

  `rsync -azvhP path/to/file remote_host_name:remote_host_location`

* Transfer a directory and all its children from a remote to local:

  `rsync -r remote_host_name:remote_directory_location local_directory_location`

* Transfer directory contents \(but not the directory itself\) from a remote to local:

  `rsync -r remote_host_name:remote_folder_location/ local_folder_location`

* Transfer only updated files from remote host:

  `rsync -ru remote_host_name:remote_directory_location local_directory_location`

* Transfer file over SSH and delete local files that do not exist on remote host:

  `rsync -e ssh --delete remote_host_name:remote_file local_file`

* Transfer file over SSH and show global progress:

  `rsync -e ssh --info=progress2 remote_host_name:remote_file local_file`

### sftp

While scp in a non-interactive way to copy files between two computers or locations, Secure File Transfer Protocol \(`sftp`\) allows you to navigate and copy files interactively. Below are some usage examples provided by [TLDR](https://tldr.sh/).

* Connect to a remote server and enter an interactive command mode:

  `sftp remote_user@remote_host`

* Connect using an alternate port:

  `sftp -P remote_port remote_user@remote_host`

* Transfer remote file to the local system:

  `get /path/remote_file`

* Transfer local file to the remote system:

  `put /path/local_file`

* Transfer remote directory to the local system recursively \(works with `put` too\):

  `get -R /path/remote_directory`

* Get list of files on local machine:

  `lls`

* Get list of files on remote machine:

  `ls`

## Using Graphical Interface

Depending on whether your local computer is a Windows, Mac OS or Linux machine, there are a large number of graphical file transfer clients to move data between your local computer and the HPC cluster. The main points to remember are:

* Host/hostname/server = `hpc.cofc.edu`
* Port = 22
* Protocol = ssh/sftp/rsync

Below is a list of the most commonly used graphical file transfer applications.

### CyberDuck

[Cyberduck](https://cyberduck.io/) not only allows you transfer to/from our HPC cluster, but also many cloud platforms such as Amazon S3, OpenStack Swift, Backblaze B2, Microsoft Azure & OneDrive, Google Drive and Dropbox.

* Availability - Windows and Mac OS
* Strengths -
  * support for many protocols and storage services including cloud platforms
  * drag-and-drop
  * live editing
  * file/directory syncing
* Weakness - 
  * No multicolumn view  -- can't see local and remote host files side by side

### WinSCP

[WinSCP](https://winscp.net/eng/download.php)

* Availability - Windows
* Strengths -
  * multicolumn views
  * drag-and-drop
* Weakness -

### FileZilla

[Filezilla](https://filezilla-project.org)

* Availability - Windows
* Strengths -
  * multicolumn views
  * drag-and-drop
* Weakness -

