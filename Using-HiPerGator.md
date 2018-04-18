# Overview
Making your code run on the hipergator, and take advantage of parallel processing, takes a few steps.

1. Modifying your code to take advantage of multiple processors (not as bad as it sounds!)
2. Accessing the hipergator via ssh to run commands and transfer files
3. Testing your scripts on the dev servers.
4. Submitting your scripts as jobs

# Step 1 
## Re-writing your code to take advantage of multiple cores. 
By default R runs on a single processor. Most computers today have 4-8 processors. If you spread the work out to multiple processors you can decrease the amount of time it takes to run by significantly. For example: a script that takes 1 hour to run can potentially take 0.5 hours with 2 processors, or 15 minutes with 4 processors. To make your scripts run across multiple processors, you'll have to make some slight adjustments to your code.

If your code uses `lapply` to run your main function to many items (e.g. fitting a model to each species), you can swap it for `mclapply` from the `parallel` package without making any substantial changes. For more details and advanced uses, here are 2 short tutorials that go over this:

* [A brief foray into parallel processing with R](https://beckmw.wordpress.com/2014/01/21/a-brief-foray-into-parallel-processing-with-r/)

* [Software Carpentry Parallel Processing in R](http://resbaz.github.io/r-intermediate-gapminder/19-foreach.html)

Some quick notes: 
* If your code already uses functions and for loops, it should be very easy to make it parallel, unless each pass through the loop depends on the outcome from previous passes.
* On your own computer, never set the amount of processors used to the max available. This will take away all the processing power needed to run the operating system, browser, and other programs, and could potentially crash your computer. To test out parallel code on my computer I set the number of processors to use at 2 (out of 8 available).

# Step 2: 
### Accessing the hipergator. 

### Prerequisites
* Hipergator usage is thru a Linux command line, so you should first become familiar with command line usage. A good tutorial is available at [Software Carpentry](http://swcarpentry.github.io/shell-novice/). 

### Getting started
1. [Request an account](http://www.rc.ufl.edu/help/account-request/)

2. connect to the server with `ssh <YOUR_USERNAME>@hpg2.rc.ufl.edu` from the Unix terminal or a Windows SSH client ([more info here](https://help.rc.ufl.edu/doc/Getting_Started)). Enter your password when prompted.

3. This will take you to a Unix terminal on the login server.  This is where you can upload files and start larger jobs on other servers. You're not supposed to run big computations on this server, which you can identify by looking for "gator" next to the command prompt.

4. Starting a job:

* You can start a **batch** job using a file like the one below (based on a file from Shawn, updated by Dave). This is how you should run everything big. Once this information is in a job file on the server, you can start it with `sbatch <your job script>`. If it works, you'll get a one-line response with your job ID and will then be returned to the terminal of the login server.

* Alternatively, you can run work on the **development server** for a limited time, as described below. You can work interactively while on this server, unlike a batch job.

5. You can check on your job's status with `squeue -u <username>`. The column labeled "S" is your job status. You want this to be `R` for "running", but it can spend a while as `Q` (in the queue) before starting, especially if you request many cores. Sometimes (but not always) the output will explain why you're still in the queue (e.g. QOSMEMLIMIT if you're using too much memory).

6. Once your batch job is running, you can freely log out (or even turn off your local machine) and wait for an email telling you that it finished.  You can log back in to see the results later.

### File transfer

* Often, the easiest way to transfer files to the server is using `git clone`.

* If your files aren't in a git repository, you can use FTP or `scp`.  FTP has graphical user interfaces that allow you to drag and drop files to the server.

* If you use `scp`, the syntax for copying one file from your user folder on the server to your local folder is is `scp MY_USER_NAME@gator.hpc.ufl.edu:/home/MY_USER_NAME/PATH_TO_MY_FILE MY_LOCAL_FILENAME`. Note the space between the remote path and your local filename. If you want to  send a file in the other direction, switch the order of the local file and the remote location.  You can copy whole folders with the `-r` flag.

[More information about storage](https://www.rc.ufl.edu/about/policies/storage/)

# Step 3: 
## Testing your code on the dev servers.
If planning on interacting with Hipergator to do anything time-consuming or resource-intensive, you should log into the development server. The development server is interactive (unlike a batch job) but can use a larger amount of computing power. You can switch to the dev server with commands like those below. The maximum is 12 hours.

```
module load ufrc
srundev --time=480 --cpus-per-task=1 --mem-per-cpu=16gb
```

While you're on the dev server, you can do a test run of your code (perhaps with fewer cores) and see how much memory you'll need.

-making sure scripts can be run via command line using Rscript. Unlike in rstudio, scripts need to be able to run from beginning to end and produce a results file. When you do call Rscript, make sure to explicitly load the `methods` package, as shown below (otherwise you can get very mysterious error messages).

# Step 4 
## Submitting full batch jobs
Since 100's of people are using the hipergator cluster, access to it is organized around jobs. The idea is that your script will run for a certain time and use a certain amount of resources (RAM and processors/cores). Your jobs (with info on the script to run and the resources it will use) is submitted to a queue with this information, where it waits for those resources to free up before being run. 

Hipergator 2 job scripts look like the one below.  More information at https://wiki.rc.ufl.edu/doc/Annotated_SLURM_Script and https://wiki.rc.ufl.edu/doc/SLURM_Commands

```
#!/bin/bash

# Job name and who to send updates to
#SBATCH --job-name=<JOBNAME>
#SBATCH --mail-user=<EMAIL>
#SBATCH --mail-type=FAIL,END
#SBATCH --account=ewhite
#SBATCH --qos=ewhite-b   # Remove the `-b` if the script will take more than 4 days; see "bursting" below

# Where to put the outputs: %j expands into the job number (a unique identifier for this job)
#SBATCH --output my_job%j.out
#SBATCH --error my_job%j.err

# Number of nodes to use
#SBATCH --nodes=1

# Number of tasks (usually translate to processor cores) to use: important! this means the number of mpi ranks used, useless if you are not using Rmpi)
#SBATCH --ntasks=1 

#number of cores to parallelize with:
#SBATCH --cpus-per-task=15
#SBATCH --mem=16000
# Memory per cpu core. Default is megabytes, but units can be specified with M 
# or G for megabytes or Gigabytes.
#SBATCH --mem-per-cpu=2G

# Job run time in [DAYS]
# HOURS:MINUTES:SECONDS
# [DAYS] are optional, use when it is convenient
#SBATCH --time=72:00:00

# Save some useful information to the "output" file
date;hostname;pwd

# Load R and run a script
# Including `--default-packages=methods` is important because otherwise
# you'll get cryptic errors where R and Rscript behave differently
module load R
Rscript --default-packages=methods my_R_script.R
```

Instructions for making a SLURM job script for hipergator 2 are [here](https://wiki.rc.ufl.edu/doc/Annotated_SLURM_Script)

# Misc. 

## Priority

The supercomputer is a shared resource, and the SLURM scheduler has to decide how to divvy it up. The method they use for deciding when it's your turn to use a machine based on a metric called "FairShare." You can see your FairShare number by typing `sshare -U` in your hipergator terminal.  A FairShare of 0.5 means you've been using exactly your share. Larger numbers mean you can use more, while smaller numbers mean you're using more than your share and will be given lower priority.

Your "usage" number is an exponentially-weighted moving average of the resources you've consumed, with a half-life of two weeks. So if you've "bursted" at 10x for a while, it might take a few weeks before you're given decent priority again.  

A more comprehensive description of FairShare is available [here](https://slurm.schedmd.com/priority_multifactor.html#fairshare).

## Bursting

If your jobs will take less than 4 days, you can use "burst" mode, which provides *ten times* as many cores and *ten times* as much memory as the default mode. If you cannot burst, just remove the `-b` from the line above about `qos`.

## Current usage  

To see the current usage by our group, as well as overall hipergator usage, use the command  

`slurmInfo -pu`  

A nice website showing the status of all jobs in the group is available [here](https://access.rc.ufl.edu/jobstatus/)

To see the total available resources use: 

`sacctmgr show qos ewhite format="Name%-16,GrpSubmit,MaxWall,GrpTres%-45"`   
for the normal queue, and    
`sacctmgr show qos ewhite-b format="Name%-16,GrpSubmit,MaxWall,GrpTres%-45"`   
for the "burst" queue.   

## Installing R packages

HiPerGator has a lot of packages installed already, but you might need to install your own, or you might want an updated version of an existing package.

You can tell R to prefer your personal library of R packages over the (possibly outdated) ones maintained for Hipergator by adding `libPaths(c("/home/YOUR_USER_NAME/R_libs", .libPaths()))` to your `.Rprofile`.  If you don't have one yet, you can create a new file with that name and put it in your home directory (e.g. in `/home/harris.d/.Rprofile`).

Once this is set up, you can install or update packages the usual way (e.g. with `install.packages` or `devtools::install_github`).

If you need an R package from CRAN but can't install it yourself (e.g. because of dependencies or compiler issues), you can always [file a support request](https://support.rc.ufl.edu/enter_bug.cgi).

# Storage

Your home folder only has a few gigabytes of disk space, but there is a large amount of space available under `/ufrc/ewhite/<your username>`. If you prefer a Dropbox-like interface, you can also hook GatorBox up to HiperGator using [these instructions](https://wiki.rc.ufl.edu/doc/GatorBox:_Adding_external_storage).

# Connecting through jupyter notebooks.

Its useful to be able to interact with hipergator, without having to rely solely on the terminal. Especially when dealing with large datasets, instead of prototyping locally, then pushing to the cloud, we can connect directly using a jupyter notebook.

* Log on to hipergator and request an interactive session.

```
srun --ntasks=1 --cpus-per-task=2 --mem=2gb -t 90 --pty bash -i
```

Now we have 90 minutes work directly on this development node.

* Create a juypter notebook

Load the python module

```
module load python
```

Start the notebook and get your ssh tunnel

```
import socket
import subprocess
host = socket.gethostname()
proc = subprocess.Popen(['jupyter', 'lab', '--ip', host, '--no-browser'])

print("ssh -N -L 8888:%s:8888 -l b.weinstein hpg2.rc.ufl.edu" % (host))
```

If all went well it should look something like:

```
[b.weinstein@c27b-s2 dask-jobqueue]$ python
Python 3.6.4 |Anaconda, Inc.| (default, Jan 16 2018, 18:10:19) 
[GCC 7.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import socket
>>> import subprocess
>>> host = socket.gethostname()
>>> proc = subprocess.Popen(['jupyter', 'lab', '--ip', host, '--no-browser'])
>>> 
>>> print("ssh -N -L 8888:%s:8888 -l b.weinstein hpg2.rc.ufl.edu" % (host))
ssh -N -L 8888:c27b-s2.ufhpc:8888 -l b.weinstein hpg2.rc.ufl.edu
>>> [I 17:11:29.776 LabApp] The port 8888 is already in use, trying another port.
[I 17:11:29.799 LabApp] JupyterLab beta preview extension loaded from /home/b.weinstein/miniconda3/envs/pangeo/lib/python3.6/site-packages/jupyterlab
[I 17:11:29.799 LabApp] JupyterLab application directory is /home/b.weinstein/miniconda3/envs/pangeo/share/jupyter/lab
[I 17:11:29.809 LabApp] Serving notebooks from local directory: /home/b.weinstein/dask-jobqueue
[I 17:11:29.809 LabApp] 0 active kernels
[I 17:11:29.809 LabApp] The Jupyter Notebook is running at:
[I 17:11:29.809 LabApp] http://c27b-s2.ufhpc:8889/?token=0c9c992a219e1e35ddd4cbe782d7f1f56c6680118b13053c
[I 17:11:29.809 LabApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 17:11:29.811 LabApp] 
    
    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://c27b-s2.ufhpc:8889/?token=0c9c992a219e1e35ddd4cbe782d7f1f56c6680118b13053c
```

see that line ssh..., that is what we need to enter in our local laptop. It will ask for your login password

```
MacBook-Pro:~ ben$ ssh -N -L 8888:c27b-s2.ufhpc:8888 -l b.weinstein hpg2.rc.ufl.edu
b.weinstein@hpg2.rc.ufl.edu's password: 
```

Don't worry if it looks like it hangs, the tunnel is open! Go check it out.

Opening your browner, go to localhost:8888

and viola, we are navigating hipergator from the confines of our own laptop.
