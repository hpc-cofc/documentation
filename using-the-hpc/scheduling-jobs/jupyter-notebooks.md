# Jupyter Notebooks

## Introduction

[Anaconda's distribution](https://www.anaconda.com/distribution/) of Python claims to be the most popular platform for data science and machine learning. It supports a lot of packages and has tools to easily manage these packages and environments. Some of its advantages include

* Ease of managing packages, dependences and environments using `Conda`
* Support for machine learning and deep learning models with `scikit-learn`, `TensorFlow`, and `Theano`
* Integration `Dask`, `NumPy`, `pandas`, and `Numba` for scalability
* Support for visualization and analysis tools such as `Matplotlib`, `Bokeh`, `Datashader`, and `Holoviews`

Below, we will describe how to run Anaconda's version of Python on the CofC cluster using [Jupyter Notebooks](https://www.jupyter.org). You will start a Jupyter notebook server on a compute node from the command line and connect to your notebook using a local browser of your workstation/laptop. This documentation is based on an example at [Harvard's HPC FAS-RC](https://www.rc.fas.harvard.edu/jupyter-notebook-server-on-odyssey/)

### General steps

Below are the steps involved in being able to run a Python notebook on our HPC using Anaconda Jupyter Notebooks 

1. **First time set up**
   1. Load the Anaconda environment. We have different `anaconda2` and `anaconda3` versions. It is best to use the latest one as long as there are no compatibility issues with the packages/libraries you intend to install and run.
      1. Create the kernel/environment you need. For example, you can install `Python2` or `Python3`, or `Haskell` or `Julia` or `R` ...etc environments depending on what codes you intend to use
   2. Since your anaconda environment is contained locally in your account \(`~/.conda`\) , you can install or uninstall these environments and any packages within them as necessary. You do not need a system administrator's permission or input to manage these environments.
2. **Running applications**
   1. Once you have the anaconda environment you need, you can
      1. load the `anaconda2`/`anaconda3` module, 
      2. activate the environment of choice
      3. start an interactive SLURM session to reserve a compute resource
      4. set up SSH port forwarding between the compute resource and your local computer \(laptop/desktop\)
      5. start a Jupyter Notebook
      6. access the Jupyter Notebook via your web browser on your local computer.
      7. run your notebook on the HPC as if it were on your local computer.

These steps may look complicated, but we have scripts that make everything easier. Everyone needs to go through the [first time set up](jupyter-notebooks.md#first-time-set-up) step below. After that, there is an easier way to run calculations using scripts, or a more involved way which outlines the actual steps that are incorporated into the scripts.

## First time set up

The first time you use Anaconda and its distribution of Python/R, you need to perform the following tasks on the master/head node.

### Anaconda versions

#### See what versions of Anaconda are available

```bash
$user@hpc[~]:    module spider anaconda

---------------------------------------------------------------------
    anaconda/3:
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
     Versions:
        anaconda/3/2019.03
        anaconda/3/2019.10
        anaconda/3/2020.02
----------------------------------------------------------------------

    This module can be loaded directly: module load anaconda2/2019.03

----------------------------------------------------------------------
    anaconda/2: anaconda/2/2019.03
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    This module can be loaded directly: module load anaconda/2/2019.03
```

If you plan to run Python3 notebooks, load up the `anaconda/3` module.

```bash
$user@hpc[~]:    module load anaconda/3/2020.02
```

### Python/R versions

Initially, only the base version of Anaconda is installed in a central/shared location. If you type `conda env list`, you will only see the base installation.

```bash
$user@hpc[~]:     conda env list
# conda environments:
#
base                  *  /opt/ohpc/pub/apps/anaconda/3/2020.02
```

Depending on your needs, you would need to install specific versions of Python and R. Anaconda uses the `conda` tool to install packages and manage your software environment. In this particular case, we'll install a Python 3.7 environment.

```bash
$user@hpc[~]:    module load anaconda/3/2020.02

$user@hpc[~]:    conda create -n myJupyter_3.7 python=3.7 jupyter
```

You will see that Python 3.7 has successfully installed by checking the list of available environments.

```bash
user@hpc[~]:    conda env list
# conda environments:
#
jupyter_3.7              /home/user/.conda/envs/myJupyter_3.7
base                  *  /opt/ohpc/pub/apps/anaconda/3/2020.02
```

To activate this environment, you can use the following command:

```bash
$user@hpc[~]:    source activate myJupyter_3.7
```

## **Running your notebook**

After performing the tasks above once the first time you use Anaconda's Python distribution, you will not need to repeat them. You can proceed with running your notebook the easy way using scripts or the more involved way, if you want more control and are up to the challenge. The steps go as follows:

1. load the `anaconda2`/`anaconda3` module,
2. activate the environment of choice
3. start an interactive SLURM session to reserve a compute resource
4. set up SSH port forwarding between the compute resource and your local computer \(laptop/desktop\)
5. start a Jupyter Notebook
6. access the Jupyter Notebook via your web browser on your local computer.
7. run your notebook on the HPC as if it were on your local computer.

###  The easy way using scripts

There are two interactive shell scripts that will allow you to run your notebooks. The steps are

1. go to the location where your notebook resides 
2. reserve computer time to run your notebook \( `request-interactive.sh`\)
3. start running your notebook to load up the Anaconda and Python environments easily \( `run-jupyter-notebook.sh`\)

#### Reserve computer time

Running a simple interactive shell script \(`reserve-interactive.sh`\) allows you to reserve resources to run your Jupyter Notebook as shown in the following example.

```bash
$user@hpc[~/test]  request-interactive.sh

This script helps you start up an interactive SLURM session to reserve 
computational resources  the CofC HPC.

How many hours do you want to reserve a server for?  Options: 1-48

2
   Reserving a node for 2 hours
How many computing cores do you need? Options: 1-40
4
   Requesting 4 core(s)
What name would you like to give this calculation? Eg. testML
0-test

Reserving computational resources using the following command
srun --wait=0 --pty -p stdmemq --ntasks=4 -t 2:00:00 -J test bash

   Please note that you should exit the notebook when you are finished.
   Otherwise, the queue manager will terminate the notebook when the time 
   you reserved runs out.
```

#### Run your notebook 

A simple interactive shell script \(`run-jupyter-notebook.sh`\) guides you through the process of initiating your Jupyter Notebook run.

```bash
$user@hpc[~/test]  run-jupyter-notebook.sh

Which version of Anaconda would you like to run.
Enter selection [0-2]:

    1. anaconda2
    2. anaconda3
    0. Quit

2
   loading anaconda3 module

Currently Loaded Modules:
  1) autotools   2) prun/1.2   3) gnu8/8.3.0   4) openmpi3/3.1.3   5) ohpc   6) use.own   7) anaconda/3/2020.02

You have these environments to pick from

myJupyter_3.7              /home/user/.conda/envs/myJupyter_3.7
base                  *  /opt/ohpc/pub/apps/anaconda/3/2020.02

Which environment would you like to use?

myJupyter_3.7

On your local computer (laptop/desktop), set up SSH port forwarding using the 
following command.

   1. Open a second terminal
   2  Copy and paste the command below into the terminal on your local laptop/desktop.

   Please note that the terminal will 'hang' once the SSH tunnel is set up.
   So, you would not be able to interact with it.

   Please do not close the terminal as that would close the SSH port forwarding 
   between your local computer and the HPC

Copy and paste the following command on your local computer:
ssh -NL 19620:hpc.cofc.edu:19620 user@hpc.cofc.edu

A Jupyter notebook will start up shortly. You will be given instructions such as this

    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-9192-open.html
    Or copy and paste one of these URLs:
        http://...
     or http://...

When you are finished with your calculation
   1. Use 'Control-C' to stop this server and shut down all kernels 
   (twice to skip confirmation).
   2. Log out of the compute node using by typing 'exit'
   3. Close the SSH port forwarding on your local computer by entering 'Control-C'


[I 19:04:17.442 NotebookApp] Loading IPython parallel extension
[I 19:04:17.443 NotebookApp] Serving notebooks from local directory: /home/user/test
[I 19:04:17.443 NotebookApp] The Jupyter Notebook is running at:
[I 19:04:17.443 NotebookApp] http://hpc.cofc.edu:19620/?token=c4bb51f28e8ee836d8101b02cb9d344c98967ea0a4e9d
[I 19:04:17.443 NotebookApp]  or http://127.0.0.1:19620/?token=c4bb518ee836d8101b02cb9d344c98967ea0a4e9d
[I 19:04:17.443 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 19:04:17.448 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-168451-open.html
    Or copy and paste one of these URLs:
        http://hpc.cofc.edu:19620/?token=c4bb51f20e68e8ee8cb9d344c98967ea0a4e9d
     or http://127.0.0.1:19620/?token=c4bb51f20e68e8ee836d810d344c98967ea0a4e9d
[I 19:04:33.423 NotebookApp] 302 GET /?token=c4bb51f20e68e8ee836d8101b02cb9d344c98967ea0a4e9d (172.16.0.1) 0.40ms
[E 19:04:33.466 NotebookApp] Could not open static file ''
[W 19:04:33.623 NotebookApp] 404 GET /static/components/react/react-dom.production.min.js (172.16.0.1) 5.19ms referer=http://127.0.0.1:19620/tree?token=c4bb51f20e68e8ee836d8101b02cb9d344c98967ea0a4e9d
[W 19:04:33.657 NotebookApp] 404 GET /static/components/react/react-dom.production.min.js (172.16.0.1) 0.87ms referer=http://127.0.0.1:19620/tree?token=c4bb51f20e68e8ee836d8101b02cb9d344c98967ea0a4e9d
[W 19:04:36.359 NotebookApp] 404 GET /static/components/react/react-dom.production.min.js (172.16.0.1) 1.63ms referer=http://127.0.0.1:19620/notebooks/Data_echo -e "
Cleaning_using_Python_with_Pandas_Library.ipynb
[W 19:04:36.436 NotebookApp] 404 GET /static/components/react/react-dom.production.min.js (172.16.0.1) 0.84ms referer=http://127.0.0.1:19620/notebooks/Data_Cleaning_using_Python_with_Pandas_Library.ipynb
[I 19:04:37.769 NotebookApp] Kernel started: 092b9b5f-4b02-4a97-8f11-d31d0076aed5
[I 19:04:38.153 NotebookApp] Adapting from protocol version 5.1 (kernel 092b9b5f-4b02-4a97-8f11-d31d0076aed5) to 5.3 (client).
[I 19:04:49.097 NotebookApp] Starting buffering for 092b9b5f-4b02-4a97-8f11-d31d0076aed5:fc649ff7bb2840438168f502ab8b5c0b
[I 19:04:49.309 NotebookApp] Kernel restarted: 092b9b5f-4b02-4a97-8f11-d31d0076aed5
[I 19:04:49.683 NotebookApp] Adapting from protocol version 5.1 (kernel 092b9b5f-4b02-4a97-8f11-d31d0076aed5) to 5.3 (client).
[I 19:04:49.684 NotebookApp] Restoring connection for 092b9b5f-4b02-4a97-8f11-d31d0076aed5:fc649ff7bb2840438168f502ab8b5c0b
[I 19:04:49.684 NotebookApp] Replaying 10 buffered messages
^C[I 19:05:25.752 NotebookApp] interrupted
Serving notebooks from local directory: /home/user/test
1 active kernel
The Jupyter Notebook is running at:
http://hpc.cofc.edu:19620/?token=c4bb51f20e68e8ee01b02cb9d344c98967ea0a4e9d
 or http://127.0.0.1:19620/?token=c4bb51f20e68e8eb02cb9d344c98967ea0a4e9d
Shutdown this notebook server (y/[n])? y
[C 19:05:28.171 NotebookApp] Shutdown confirmed
[I 19:05:28.173 NotebookApp] Shutting down 1 kernel
[I 19:05:28.474 NotebookApp] Kernel shutdown: 092b9b5f-4b02-4a97-8f11-d31d0076aed5

When you are finished with your calculation
   1. Use 'Control-C' to stop this server and shut down all kernels 
   (twice to skip confirmation).
   2. Log out of the compute node using by typing 'exit'
   3. Close the SSH port forwarding on your local computer by entering 'Control-C'

```

### The hard way

#### Run test on the master node

You are probably on the master/login node at this point and you can run quick, simple tests there. All your heavy calculations need to be submitted to a compute note using the SLURM batch scheduler. We'll get to that in the next stage. For now, let's do an interactive run on the master node.

_**Set up the calculation**_

**On the server side**

1. Load up and activate the environment on the server/node
   * ```sql
     $user@hpc[~]:  module load anaconda/3/2020.02

     $user@hpc[~]:  conda activate myJupyter_3.7
     ```
2. Set up forwarding of the notebook data over an unused port \(say `10002`\)
   * ```sql
     $user@hpc[~]:  export myport=10002
     ```
   * You can determine the exact port forwarding command by executing the command below: \[1\] 
     * ```sql
       $user@hpc[~]:  echo "ssh -NL $myport:$(hostname):$myport $USER@hpc.cofc.edu"
       ```
3. Start the notebook
   * ```sql
     $user@hpc[~]:  jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'
     ```
4. You should see something like that looks like this:

```bash
$(jupyter_3.7) user@hpc[~]:  jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'

[I 12 NotebookApp] Serving notebooks from local directory: /home/bt-local
[I 12 NotebookApp] The Jupyter Notebook is running at:
[I 12 NotebookApp] http://hpc.cofc.edu:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12 NotebookApp]  or http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 12 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-274617-open.html
    Or copy and paste one of these URLs:
        http://hpc.cofc.edu:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
     or http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
```

Before you connect notebooks using the above URLs, you need to start SSH forwarding on your local desktop/laptop

**On the client side \(your laptop/desktop\)**

1. In a new terminal on your laptop/desktop, start an SSH tunnel between the server \(master node\) and your local machine using the command from \[1\]. 
2. It should look something like this:
   1. ```sql
      user@laptop[~]:  ssh -NL 10002:hpc.cofc.edu:10002 $USER@hpc.cofc.edu
      ```
3. * You will be prompted for a password unless you have SSH keys already set up. **Please note that you will not see any output if the connection is successful. Please keep the terminal alive and open your browser to access your notebook**
4. Point your browser to the URL provided above in \[2\]
   * Eg.  [http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01](http://127.0.0.1:10002/?token=7efb536faedf2e36e849cb39150f32300ad7ac9253ed7f01)

#### Run on compute nodes interactively

You need to run your production calculations on compute nodes by first starting an interactive session.

#### Set up the calculation

**On the server side**

1. Start an interactive session using a command like this:
   * ```sql
     user@hpc[~]:  srun --pty -p stdmemq -n 20 -t 00-08:00:00 --ntasks=1 --pty --mem=48000 bash
     ```
2. Load up and activate the environment on the server/node
   * ```sql
     user@hpc[~]:  module load anaconda/3/2020.02
     user@hpc[~]:  conda activate myJupyter_3.7
     ```
3. Set up forwarding of the notebook data over an unused port \(say `10002`\)
   * ```sql
     user@hpc[~]:  export myport=10002
     ```
   * You can determine the exact port forwarding command by executing the command below: \[1\]
     * ```sql
       user@hpc[~]:  echo "ssh -NL $myport:$(hostname):$myport $USER@hpc.cofc.edu"
       ```
4. Start the notebook
   * ```sql
     user@hpc[~]: jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'
     ```

You should see something like that looks like this:

```bash
$(jupyter_3.7) user@hpc[~]  jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'

[I 12 NotebookApp] Serving notebooks from local directory: /home/bt-local
[I 12 NotebookApp] The Jupyter Notebook is running at:
[I 12 NotebookApp] http://host.cofc.edu:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12 NotebookApp]  or http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 12 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-274617-open.html
    Or copy and paste one of these URLs:
        http://host.cofc.edu:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
     or http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
```

Before you connect notebooks using the above URLs, you need to start SSH forwarding on your local desktop/laptop

**On the client side \(your laptop/desktop\)**

* In a new terminal on your laptop/desktop, start an SSH tunnel between the server \(master node\) and your local machine using the command from \[1\]. It should look something like
* ```sql
  user@laptop[~] .  ssh -NL 10001:hpc.cofc.edu:10002 $USER@hpc.cofc.edu
  ```

  * You will be prompted for a password unless you have SSH keys already set up. **Please note that you will not see any output if the connection is successful. Please keep the terminal alive and open your browser to access your notebook**
* Point your browser to the URLs provided above
  * Eg.  [http://127.0.0.1:10002/?token=7efb536faedf2e36e849cb39150f32300ad7ac9253ed7f01](http://127.0.0.1:10002/?token=7efb536faedf2e36e849cb39150f32300ad7ac9253ed7f01)

