# Customize Environment

The Bash shell environment may be customized to suit your needs.

## Initialize your environment

Our cluster utilizes Bash as the default shell and when a session started it reads commands from `~/.bashrc`and `~/.bash_profile.`

Environment variables are set in the file `~/.bashrc`.

You can also set aliases `~/.bash_aliases`

📝 **Note:** The files `~/.bash_profile` and `.bashrc` are hidden. To list hidden files, type `ls -a`.

## Know the environment variables

Here is a list of some common environment variables:

* `$HOME` - Path of your home directory
* `$PATH` - List of directories where the system checks for programs to run
* `$LD_LIBRARY_PATH` - List of directories where the system checks for shared libraries to load
* `$HOSTNAME` - The name of the host machine.

To see all your environment variables, typing `env` in your terminal.

```bash
$user@hpc[~]:   env
PATH=
LD_LIBRARY_PATH=
MANPATH=
HOSTNAME=
TERM=xterm-256color
SHELL=/bin/bash
PWD=
HISTSIZE=
SSH_CLIENT=
CONDA_SHLVL=1
CONDA_PROMPT_MODIFIER=(base)
LMOD_PKG=/
LMOD_VERSION=
MODULEPATH=
HOME=
...
```

## Set and modify with the environment variables

* Display the value of an environment variable using `echo`:

  ```sql
  user@hpc[~]:  echo $HOME
  /home/$USERNAME
  ```

* Set or modify the value of environment variables with `export`:

  ```sql
  user@hpc[~]:  export PATH=$PATH:/home/$USER

  user@hpc[~]:  export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/$USER/custom_lib_directory
  ```

* Set or modify a value for environment variables:

  ```sql
  user@hpc[~]:   export OMP_NUM_THREADS=8
  ```

## Set up custom environmental modules for your software

Modules are a utility which allow users to load and manage applications and their versions. The modules of software packages allow you to dynamically modify your user environment by using “modulefiles.” Each modulefile contains the information needed to configure the shell for an application.

You can learn more about system-wide modules at [Access Software](modules/)

To create module files for your own software, you can use the following steps.



### How about Users' Own Applications <a id="how-about-users-own-applications"></a>

You are welcome to install and run your own applications. Here are some useful tips

* It's best to consistently stick with one compiler and MPI library if possible.
* To ease setting up the environment to run your own applications
  * You can enter `module load use.own` to create a directory called `privatemodules` in your `$HOME` directory
  * ```sql
    user@hpc[~]:  module load use.own

    user@hpc[~]:  module list
    Currently Loaded Modules:
      1) autotools   2) prun/1.2   3) gnu8/8.3.0   4) openmpi3/3.1.3   5) ohpc   6) use.own

    user@hpc[~]:  ls
    privatemodules  sample.slurm  slurm-examples
    ```
  * You can copy an example module file from `/opt/ohpc/pub/examples/example.modulefile` or `/opt/ohpc/pub/examples/examplempi-dependent.modulefile` and change it to match your application





