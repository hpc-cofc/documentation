# Graphical Client SFTP

Graphical file transfer clients can be used to move data between your local machine and remote storage locations. Once you install the client on your computer and set up the remote connection, you may move folders and files between your computer and the remote storage using a drag-and-drop method.

## CyberDuck \(macOS and Windows\)

Download Cyberduck [here](https://cyberduck.io/) and run the installation.

<!--
_**AWS S3 - Scality**_

* To set up a new connection, click on the `Open Connection` button in the top left of the window.
* In the dropdown menu of the resulting window, select `Amazon S3`.
* For Scality, change the server field to `tigris-s3.doane.edu`.
* Paste your Access Key ID and Secret Access Key that was generated when you signed up for the AWS S3 service.
* Click `Connect`.   

   [![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/cyberduck-aws.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/cyberduck-aws.png)   

_**OpenStack Virtual Machine**_

* To set up a new connection, click on the `Open Connection` button in the top left of the window.
* In the dropdown menu of the resulting window, select `SFTP (SSH File Transfer Protocol)`.
* Server: the IP address of your virtual machine
* Username: `username`
* Password: leave blank
* Select your SSH key from the dropdown menu. Be sure to choose the SSH key that allows you to access your OpenStack virtual machine.   
* Click `Connect`.   

   [![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/cyberduck-os-vm.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/cyberduck-os-vm.png)   

_**CCLA OR Condo HPC, NFS, and Lustre**_

* To set up a new connection, click on the `Open Connection` button in the top left of the window.
* In the dropdown menu of the resulting window, select `SFTP (SSH File Transfer Protocol)`.
* Server: `tigris.doane.edu`
* Username: your  ID \(UID\)
* Password: your  password
* Select your SSH key from the dropdown menu. Be sure to choose the SSH key that allows you to access the CCLA OR HPC Condo login node.
* Click `Connect`.

  > NFS user home directory path: `~/home/UID/`  
  > Lustre storage path: `~/lustre/tigris/`

  [![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/cyberduck-condo-login.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/cyberduck-condo-login.png)  

-->

## WinSCP \(Windows\)

Download WinSCP [here](https://winscp.net/eng/download.php) and run the installation.  
📝 **Note:** In cases where an SSH key is required for access, you must store the path to the key in WinSCP for each connection. To store the key, enter the connection information that you will find in the steps below. Then, click the `Advanced...` button. Provide the path to your SSH private key.  

<!--
[![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-advanced.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-advanced.png)  

[![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-advanced-ssh-key.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-advanced-ssh-key.png)  


_**AWS S3 - Scality**_

* To set up a new connection, click on `New Site` in the top left of the window.
* In the `File protocol` dropdown menu on the right, select `Amazon S3`.
* Host name: `tigris-s3.doane.edu`
* Paste your Access Key ID and Secret Access Key that was generated when you signed up for the AWS S3 service.
* Click `Login`.   

   [![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-aws.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-aws.png)   

_**OpenStack Virtual Machine**_

* To set up a new connection, click on `New Site` in the top left of the window.
* In the `File protocol` dropdown menu  on the right, select `SFTP`.
* Host name: the IP address of your virtual machine
* User name: `username`
* Password: leave blank
* Click `Login`.  

   [![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-os-vm.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-os-vm.png)   

_**CCLA HPC, NFS, and Lustre**_

* To set up a new connection, click on `New Site` in the top left of the window.
* In the `File protocol` dropdown menu  on the right, select `SFTP`.
* Host name: the IP address of your virtual machine
* Username: your  ID \(UID\)
* Password: your  password
* Click `Login`.

  > NFS user home directory path: `~/home/UID/`  
  > Lustre storage path: `~/lustre/tigris/`

  [![](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-condo-login.png)](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/screenshots/winscp-condo-login.png)  



## Related Tutorials

* [Scality Object Storage User Guide](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/data-transfer-storage/scality-guide.md)
* [Globus Data Transfer Tool](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/data-transfer-and-storage/data-transfer-storage/globus-overview.md)
* [Access VM Instances](https://github.com/wendikristine/documentation-template/tree/62a326e16ecef2ff128ef0b976de12c16f6ea062/openstack/access-vm/access-vm.md)

-->
