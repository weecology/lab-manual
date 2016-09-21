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
* Hipergator usage is thru a Linux command line, so you should first become familiar with command line usage. A good tutorial is available at [Software Carpentry](http://swcarpentry.github.io/shell-novice/02-create.html). 

### Getting started
1. [Request an account](http://www.rc.ufl.edu/help/account-request/)

2. connect to the server with `ssh <YOUR_USERNAME>@hpg2.rc.ufl.edu` from the Unix terminal or a Windows SSH client ([more info here](http://wiki.hpc.ufl.edu/doc/Getting_Started)). Enter your password when prompted.

3. This will take you to a Unix terminal on the login server.  This is where you can upload files and start larger jobs on other servers. You're not supposed to run big computations on this server. See the section on file transfer below. 

4. You can start a job using a file like the one below (based on a file from Shawn, updated by Dave). Once this information is in a job file on the server, you can start it with `sbatch <your job script>`. If it works, you'll get a one-line response with your job ID and will then be returned to the terminal of the login server.

5. You can check on your job's status at http://rc.ufl.edu/jobstatus/ or with `squeue -u <username>`. The column labeled "S" is your job status. You want this to be `R` for "running", but it can spend a while as `Q` (in the queue) before starting, especially if you request many cores

6. Once your job is running, you can freely log out (or even turn off your local machine) and wait for an email telling you that it finished.  You can log back in to see the results later.

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

-making sure scripts can be run via command line using Rscript. Unlike in rstudio, scripts need to be able to run from beginning to end and produce a results file.

# Step 4 
## Submitting full batch jobs
Since 100's of people are using the hipergator cluster, access to it is organized around jobs. The idea is that your script will run for a certain time and use a certain amount of resources (RAM and processors/cores). Your jobs (with info on the script to run and the resources it will use) is submitted to a queue with this information, where it waits for those resources to free up before being run. 

***Script for Hipergator Version 1 removed. Archived [here](https://github.com/weecology/lab-wiki/wiki/Using-HiPerGator/f0d2ed8d33a91476ad7515d3c3486ccab91f3b01).***

Hipergator 2 job scripts look like the one below.  More information at https://wiki.rc.ufl.edu/doc/Annotated_SLURM_Script and https://wiki.rc.ufl.edu/doc/SLURM_Commands

```
#!/bin/bash

# Job name and who to send updates to
#SBATCH --job-name=<JOBNAME>
#SBATCH --mail-user=<EMAIL>
#SBATCH --mail-type=FAIL,END


# Where to put the outputs:
#   %A expands to the job-name specified above
#   %j expands into the job number (a unique identifier for this job)
#SBATCH --output %A%j.out
#SBATCH --error %A%j.err

# Number of nodes to use
#SBATCH --nodes=1

# Number of tasks (usually translate to processor cores) to use
#SBATCH --ntasks=1

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
module load R
Rscript my_R_script.R
```

Instructions for making a SLURM job script for hipergator 2 are [here](https://wiki.rc.ufl.edu/doc/Annotated_SLURM_Script)

# Misc. 

## Installing R packages

HiPerGator has a lot of packages installed already, but you might need to install your own.

### If the package is on CRAN

From R, type `install.packages("MY_PACKAGE") and select a CRAN mirror.  If you get an error saying "Warning: unable to access index for repository..." try another CRAN mirror instead.

### Non-CRAN packages

I (Dave) don't know if the following method of getting R packages installed is officially sanctioned, but it's worked for me and I haven't gotten in trouble for using it.

First, type `export R_LIBS="~/R/x86_64-unknown-linux-gnu-library/R_VERSION/"` at the login server's command line (where `R_VERSION` is the version of R you'll be using (currently 3.2).  This will tell R to put new packages in the `R` folder of your home directory. You may need to create this directory manually, with `mkdir ~/R/x86_64-unknown-linux-gnu-library/R_VERSION/`.

Next, make sure you have a source file for the package.  For CRAN packages, these can be found online under the heading "Package source:".  For other packages, you can create them with `R CMD build FOLDER_CONTAINING_MY_PACKAGE`.  Either way, you should end up with a file whose name follows the format `MY_PACKAGE_version.tar.gz`.

Finally, type `R CMD install MY_PACKAGE_version.tar.gz`.  The package will be built, along with any dependencies, and should be accessible the next time you run R.

# Storage

Your home folder only has a few gigabytes of disk space, but there is a large amount of space available under `/ufrc/ewhite/<your username>`. If you prefer a Dropbox-like interface, you can also hook GatorBox up to HiperGator using [these instructions](https://wiki.rc.ufl.edu/doc/GatorBox:_Adding_external_storage).

-----------------------------
#Hipergator 2.0 notes.

-Transferring seems very straightforward as long as your hipergator login name is the same as your gatorlink name (also the same as your ufl email). If it isn't for some reason you'll need to submit a support ticket to get the login sorted out on hipergator2. If it is then using HP2 only involves

-We do not have to move as a group. Each person can do so individually.

-Read more about transferring here https://www.rc.ufl.edu/services/computation/hipergator/user-information/. But in general you must.

1. Login into the new login node `hpg2.rc.ufl.edu` 
2. From there login to the data transfer node `dtn1`
3. cp your data out of `/scratch/lfs/<your username>` to `/ufrc/ewhite/<your username>`
    -Note you don't have to transfer things that were in your home folder. (the folder you're in when you login to either hipergator1 or 2 login nodes.).
4. `/ufrc/ewhite/<your username>` is your new folder to store large amounts of data. 
5. The old job scripts used a cluster computer software called MOAB. Which handled the scheduling of all the users and computer nodes on the system.
   Hipergator 2 will use a similar software called SLURM, which uses all the same basic ideas but some of the job script details will change. See the details of how to change job scripts [here](http://wiki.rc.ufl.edu/doc/PBS2SLURM_Command_Reference).

# Little aside: transferring data from Hypergator 1 to Hypergator 2 using rsync
As suggested in the Hypergator2.0 wiki page, transferring files from `/scratch/lfs/<your username>` to `/ufrc/ewhite/yourUser` is pretty easy. Just follow these steps:

`[yourUser@yourComputer]$ ssh yourUser@hpg2.rc.ufl.edu`

`<Enter password>`

`[yourUser@gator4 ~]$ ssh dtn1`

`[yourUser@dtn1 ~]$ rsync -av /scratch/lfs/yourName/important_data/ /ufrc/ewhite/yourUser`

