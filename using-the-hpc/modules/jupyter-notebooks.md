# Jupyter Notebooks

## Anaconda Jupyter Notebooks

[Anaconda's distribution](https://www.anaconda.com/distribution/) of Python and R claims to be the most popular platform for data science and machine learning. It supports a lot of packages and has tools to easily manage these packages and environments. Some of its advantages include

* Ease of managing packages, dependences and environments using Conda
* Support for machine learning and deep learning models with scikit-learn, TensorFlow, and Theano
* Integration Dask, NumPy, pandas, and Numba for scalability
* Support for visualization and analysis tools such as Matplotlib, Bokeh, Datashader, and Holoviews

Below, we will describe how to run Anaconda's version of Python on the CofC cluster using [Jupyter Notebooks](https://www.jupyter.org). You will start a Jupyter notebook server on a compute node from the command line and connect to your notebook using a local browser of your workstation/laptop. This documentation is based on an example at [Harvard's HPC FAS-RC](https://www.rc.fas.harvard.edu/jupyter-notebook-server-on-odyssey/)

## First time setup

The first time you use Anaconda and its distribution of Python/R, you need to perform the following tasks on the master/head node.

### Anaconda versions

#### See what versions of Anaconda are available

```sql
user@hpc[~]:    module spider anaconda

---------------------------------------------------------------------
  anaconda2: anaconda2/2019.03
----------------------------------------------------------------------

    This module can be loaded directly: module load anaconda2/2019.03

----------------------------------------------------------------------
  anaconda3: anaconda3/2019.03
----------------------------------------------------------------------
```

If you plan to run Python3 notebooks, load up the `anaconda3` module.

```sql
user@hpc[~]:    module load anaconda3/2019.03
```

### Python/R versions

Initially, only the base version of Anaconda is installed in a central/shared location. If you type `conda env list`, you will only see the base installation.

```sql
user@hpc[~]:     conda env list
# conda environments:
#
base                  *  /opt/ohpc/pub/apps/anaconda/anaconda3-2019.03
```

Depending on your needs, you would need to install specific versions of Python and R. Anaconda uses the `conda` tool to install packages and manage your software environment. In this particular case, we'll install a Python 3.7 environment.

```sql
user@hpc[~]:    module load anaconda3/2019.03
user@hpc[~]:    conda create -n jupyter_3.7 python=3.7 jupyter
```

You will see that Python 3.7 has successfully installed by checking the list of available environments.

```sql
user@hpc[~]:    conda env list
# conda environments:
#
jupyter_3.7              /home/barberca/.conda/envs/jupyter_3.7
base                  *  /opt/ohpc/pub/apps/anaconda/anaconda3-2019.03
```

To activate this environment, you can use the following command:

```sql
user@hpc[~]:    source activate jupyter_3.7
```

## After first setup

After performing the tasks above once the first time you use Anaconda's Python distribution, you will not need to repeat them. You can proceed to load up the Anaconda and Python environments easily.

### See available environments

```sql
user@hpc[~]:    conda env list
# conda environments:
#
jupyter_3.7              /home/barberca/.conda/envs/jupyter_3.7
base                  *  /opt/ohpc/pub/apps/anaconda/anaconda3-2019.03
```

### Activate the desired environment

```sql
user@hpc[~]:    source activate jupyter_3.7
```

### Run test on the master node

You are probably on the master/login node at this point and you can run quick, simple tests there. All your heavy calculations need to be submitted to a compute note using the SLURM batch scheduler. We'll get to that in the next stage. For now, let's do an interactive run on the master node.

#### Set up the calculation

**On the server side**

1. Load up and activate the environment on the server/node
   * ```sql
     user@hpc[~]:  module load anaconda3/2019.03
     user@hpc[~]:  conda activate jupyter_3.7
     ```
2. Set up forwarding of the notebook data over an unused port \(say `10002`\)
   * ```sql
     user@hpc[~]:  export myport=10002
     ```
   * You can determine the exact port forwarding command by executing the command below: \[1\] 
     * ```sql
       user@hpc[~]:  echo "ssh -NL $myport:$(hostname):$myport $USER@hpc.cofc.edu"
       ```
3. Start the notebook
   * ```sql
     user@hpc[~]:  jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'
     ```
4. You should see something like that looks like this:

```sql
(jupyter_3.7) user@hpc[~]:  jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'

[I 12:57:24.992 NotebookApp] Serving notebooks from local directory: /home/bt-local
[I 12:57:24.992 NotebookApp] The Jupyter Notebook is running at:
[I 12:57:24.992 NotebookApp] http://hpc.cofc.edu:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12:57:24.992 NotebookApp]  or http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12:57:24.992 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 12:57:24.998 NotebookApp]

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

### Run on compute nodes interactively

You need to run your production calculations on compute nodes by first starting an interactive session.

#### Set up the calculation

**On the server side**

1. Start an interactive session using a command like this:
   * ```sql
     user@hpc[~]:  srun --pty -p stdmemq -n 20 -t 00-08:00:00 --ntasks=1 --pty --mem=48000 bash
     ```
2. Load up and activate the environment on the server/node
   * ```sql
     user@hpc[~]:  module load anaconda3/2019.03
     user@hpc[~]:  conda activate jupyter_3.7
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

```sql
(jupyter_3.7) user@hpc[~]  jupyter-notebook --no-browser --port=$myport --ip='0.0.0.0'

[I 12:57:24.992 NotebookApp] Serving notebooks from local directory: /home/bt-local
[I 12:57:24.992 NotebookApp] The Jupyter Notebook is running at:
[I 12:57:24.992 NotebookApp] http://host.cofc.edu:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12:57:24.992 NotebookApp]  or http://127.0.0.1:10002/?token=7e2e36e849cb39150f32300ad7ac9253ed7f01
[I 12:57:24.992 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 12:57:24.998 NotebookApp]

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

