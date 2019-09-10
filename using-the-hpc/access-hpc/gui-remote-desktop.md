# GUI - remote desktop

#### Graphical user interface \(GUI\)

GUIs enable users to compute on the cluster using little or no command line tools. These graphical access options come in two forms:

* Remote desktop sessions
* Web interface

**Remote desktop sessions**

We have a [Cendio Thinlinc ](https://www.cendio.com/)remote desktop server running on the cluster to provide users access to a graphical Linux environment. _We only have 5 concurrent licenses, so please close the remote desktop session and exit as soon as you are finished._ Users would need to download and install a Thinlinc Client from the [Cendio site](https://www.cendio.com/thinlinc/download). There are Thinlinc Clients for Windows, MacOS and Linux.

After installing the Thinlinc Client, you can start the application and provide the necessary information to start the remote desktop session.

![ThinLinc Client login window](../../.gitbook/assets/thinlinc-client-login%20%281%29.png)

To ensure optimal usage without consuming a lot of resources on the client as well as server side, we recommend that you make the following changes to the under '**Options**'.

![Disable exporting all local resources](../../.gitbook/assets/thinlinc-client-disable-audio.png)

![If you have set up SSH keys, please choose &apos;public key&apos; authentication](../../.gitbook/assets/thinlinc-client-security-usesshkeys%20%281%29.png)

![Disable &apos;Full screen mode&apos;](../../.gitbook/assets/thinlinc-client-disable-fullscreen%20%281%29.png)

After you provide all the necessary information to log in, you will be asked to pick a 'Profile' or desktop manager. To prevent these remote desktop from taking too many resources in the login node, we suggest that you use a clean and lightweight desktop like XFCE.

![Pick the XFCE desktop manger](../../.gitbook/assets/thinlinc-client-pick-dm.png)

Once you have picked a 'profile' or desktop manager, you should see a Linux remote desktop environment.

![XFCE remote desktop environment](../../.gitbook/assets/thinlinc-client-rdsession.png)

**Note:** _Because we only have 5 concurrent licenses, please close the remote desktop session and exit as soon as you are finished._

