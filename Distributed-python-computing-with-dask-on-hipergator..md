
# Aim
We often have very large datasets that need to be handled using our high performance computing system. We also want to comfort of working on out laptops, and not being tied to the command line. The goal of this wiki page is to outline how to use dask and juypterlab notebooks to manipulate spatial data on hipergator. This is an evolving document that will be updated as we find best practices.
 
## Setup

* Log on to hipergator.

* Start an interactive node.

```
srun --ntasks=1 --cpus-per-task=2 --mem=2gb -t 90 --pty bash -i
```

* Create a conda virtual environment. We want some control over our own python environment, and not be so dependent on the python modules provided by admin. Start in our home directory

```
cd ~

wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
```

We can use the wonderful pangeo environment to install dask and some useful tools. See the [pangeo](https://pangeo-data.github.io/) github wiki for more info. 

```
conda create -n pangeo -c conda-forge \
    python=3.6 dask distributed xarray jupyterlab mpi4py
```

Start the conda environment

```
source activate pangeo
```

* Start a dask worker

```
from dask_jobqueue import SLURMCluster
from datetime import datetime
from time import sleep

cluster = SLURMCluster(project='ewhite',death_timeout=200)
cluster.start_workers(1)

print(cluster.job_script())

from dask.distributed import Client
client = Client(cluster)
    
import socket
host = client.run_on_scheduler(socket.gethostname)

def start_jlab(dask_scheduler):
    import subprocess
    proc = subprocess.Popen(['jupyter', 'lab', '--ip', host, '--no-browser'])
    dask_scheduler.jlab_proc = proc

client.run_on_scheduler(start_jlab)

print("ssh -N -L 8787:%s:8787 -L 8888:%s:8888 -l b.weinstein hpg2.rc.ufl.edu" % (host, host))
```

yields

```

```

see that line ssh..., that is what we need to enter in our local laptop. It will ask for your login password

```
MacBook-Pro:~ ben$ ssh -N -L 8888:c27b-s2.ufhpc:8888 -l b.weinstein hpg2.rc.ufl.edu
b.weinstein@hpg2.rc.ufl.edu's password: 
```

Don't worry if it looks like it hangs, the tunnel is open! Go check it out.

Opening your browser, go to localhost:8888

and viola, we are navigating hipergator from the confines of our own laptop.