# Services

_Before checking the status of the SSH service, make sure you have the SSHD service enabled._

* **Turning ON the SSHD service at boot time**

  ```bash
  systemctl enable sshd.service
  ```

  _To turn it off at boot time, please enter_ `systemctl disable sshd.service`_._

* **Check if a service is enabled or disabled**

  ```bash
  systemctl status sshd.service
  ```

  _It will display a message of **active** or **inactive** service._

* **Reload SSHD configuration changes**

  ```bash
  systemctl start sshd.service
  systemctl restart sshd.service
  systemctl stop sshd.service
  systemctl reload sshd.service
  ```

  _The_ `start` _option will initiate the SSHD service,_ `stop` _will stop it, and finally,_ `restart` _or_ `reload` _will refresh the new configurations_.

