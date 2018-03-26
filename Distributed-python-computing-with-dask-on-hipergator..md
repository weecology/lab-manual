# Aim

We often have very large datasets that need to be handled using our high performance computing system. We also want the comfort of working on our laptops, and not being tied to the command line. The goal of this wiki page is to outline how to use dask and juypterlab notebooks to manipulate spatial data on hipergator. This is an evolving document that will be updated as we find best practices.
 
## Initial Setup (only need to do once)

* Log on to hipergator.
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

Install dask-jobqueue. This helps boot a worker from python. Very useful. We are temporarily using a fork until upstream changes that match our needs are merged.

```
module load git 
pip install git+https://github.com/bw4sz/dask-jobqueue.git
```

## Start a Jupyter notebook

* Start an interactive node

```
module load ufrc
srun --ntasks=1 --cpus-per-task=2 --mem=2gb -t 90 --pty bash -i
```

* Activate your conda environment

```
conda activate pangeo
```

Open Python and run:

```
import getpass
import socket
import subprocess
host = socket.gethostname()
proc = subprocess.Popen(['jupyter', 'lab', '--ip', host, '--no-browser'])

print("ssh -N -L 8787:{0}:8787 -L 8888:{0}:8888 -l {1} hpg2.rc.ufl.edu".format(host, getpass.getuser()))
```

Copy the output (`ssh...`) and run that line on your local machine. It will ask for your login password. E.g.,

```
$ ssh -N -L 8888:c27b-s2.ufhpc:8888 -l HPCUSERNAME hpg2.rc.ufl.edu
HPCUSERNAME@hpg2.rc.ufl.edu's password: 
```

(HPCUSERNAME will have been automatically replaced with your HiperGator username.

Don't worry if it looks like it hangs, the tunnel is open! Go check it out.

Opening your browser, go to localhost:8888, its a notebook in the cloud!

## Start a dask worker

```
from dask_jobqueue import SLURMCluster
cluster = SLURMCluster(project='ewhite',death_timeout=100,threads_per_worker=2,processes=4)
```

Hipergator seems pretty finicky with threading, the following settings (which can all be passed as arguments to `SLURMCluster`) seem to work well.

```
{'base_path': '/home/b.weinstein/miniconda3/envs/pangeo/bin',
 'death_timeout': 100,
 'extra': '',
 'memory': '7GB',
 'name': 'dask',
 'processes': 1,
 'project': 'ewhite',
 'scheduler': 'tcp://172.16.192.13:34351',
 'threads_per_worker': 4,
 'walltime': '00:30:00'}
```

Add worker(s)

```
from dask.distributed import Client
client = Client(cluster)
```

This adds one worker. I recommended adding atleast 3.

```
cluster.start_workers(1)
client
```

A call to client should return some info on the CPU and memory of workers.
Dask provides a great client to check out the worker.

open up localhost:8787/status to see the dask dashboard. For worker

## Known Errors

* If the number of processes is too high, the client will initially grab workers and then shed them? I submitted an IT ticket, I believe this is memory use, but not sure. 8 processes with 4 threads-per-worker fails. It appears that multiple nodes of single multi-threaded workers is the best solution. That is, in SLURMCluster, processes=1, threads_per_worker > 1, and then requesting multiple nodes with cluster.start_workers().

see

https://github.com/dask/dask-jobqueue/issues/20#issuecomment-375770094

