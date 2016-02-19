1. [Request an account](http://www.rc.ufl.edu/help/account-request/)

2. connect to the server with `ssh <YOUR_USERNAME>@gator.hpc.ufl.edu` from the Unix terminal or a Windows SSH client ([more info here](http://wiki.hpc.ufl.edu/doc/Getting_Started)). Enter your password when prompted.

3. This will take you to a Unix terminal on the login server.  This is where you can upload files and start larger jobs on other servers. You're not supposed to run big computations on this server. See the section on file transfer below. 

4. You can start a job using a file like the one below (based on a file from Shawn, updated by Dave). Once this information is in a job file on the server, you can start it with `qsub <your job script>`. If it works, you'll get a one-line response with your job ID and will then be returned to the terminal of the login server.

5. You can check on your job's status at http://rc.ufl.edu/jobstatus/ or with `qstat -u <username>`. The column labeled "S" is your job status. You want this to be `R` for "running", but it can spend a while as `Q` (in the queue) before starting, especially if you request many cores

6. Once your job is running, you can freely log out (or even turn off your local machine) and wait for an email telling you that it finished.  You can log back in to see the results later.

## File transfer

* Often, the easiest way to transfer files to the server is using `git clone`.

* If your files aren't in a git repository, you can use FTP or `scp`.  FTP has graphical user interfaces that allow you to drag and drop files to the server.

* If you use `scp`, the syntax for copying one file from your user folder on the server to your local folder is is `scp MY_USER_NAME@gator.hpc.ufl.edu:/home/MY_USER_NAME/PATH_TO_MY_FILE MY_LOCAL_FILENAME`. Note the space between the remote path and your local filename. If you want to  send a file in the other direction, switch the order of the local file and the remote location.  You can copy whole folders with the `-r` flag.

[More information about storage](https://www.rc.ufl.edu/about/policies/storage/)


## Sample job script

```
#!/bin/sh
#These are variables to pass to the job handler, see http://wiki.rc.ufl.edu/doc/Annotated_PBS_Script and
#http://wiki.rc.ufl.edu/doc/PBS_Directives for more details

#Do not rerun the job if it fails
#PBS -r n

#The name of the job
#PBS -N JOBNAME

#The file that output will be written to
#PBS -o JOBNAME.out

#The file that errors will be written to
#PBS -e JOBNAME.err

#Notifications options. a=notify when job is aborted, b=notify when job begins, e=notify when job terminates
#PBS -m abe

#Email to send notifications to
#PBS -M YOUR.EMAIL@ufl.edu

#These are the important ones, the amount of resources you want to use.
#Nodes are the number of seperate servers that you want to use. ppn is processors per node.
#Using more than 1 node requires your script to have cross server communication built into it, so for most work we'll
#probably just use single nodes.
#ppn should match the number of threads/cores you setup in your script. Our max for the lab at the moment is 32.
#PBS -l nodes=1:ppn=N_CORES_PER_NODE

#The amount of memory that your script will require. This can be just a rough guess with some buffer added on.
#8192mb is a reasonable starting value, if you're not sure and you think your script could run on a laptop.
#PBS -l pmem=MEMORYmb

#The length of time your script will run. again this can be a rough guess with some buffer time added.
#PBS -l walltime=HOURS:MINUTES:SECONDS

#Set the working directory of the job to your current working directory
cd $PBS_O_WORKDIR

#Loads R
module load R

#The actual command to run your script like you would from the command line.
Rscript "MY_FILE.R"
```

## Installing R packages

HiPerGator has a lot of packages installed already, but you might need to install your own.

### If the package is on CRAN

From R, type `install.packages("MY_PACKAGE") and select a CRAN mirror.  If you get an error saying "Warning: unable to access index for repository..." try another CRAN mirror instead.

### Non-CRAN packages

I (Dave) don't know if the following method of getting R packages installed is officially sanctioned, but it's worked for me and I haven't gotten in trouble for using it.

First, type `export R_LIBS="~/R"` at the login server's command line.  This will tell R to put new packages in the `R` folder of your home directory. You may need to create this directory manually, with `mkdir ~/R`.

Next, make sure you have a source file for the package.  For CRAN packages, these can be found online under the heading "Package source:".  For other packages, you can create them with `R CMD build FOLDER_CONTAINING_MY_PACKAGE`.  Either way, you should end up with a file whose name follows the format `MY_PACKAGE_version.tar.gz`.

Finally, type `R CMD install MY_PACKAGE_version.tar.gz`.  The package will be built, along with any dependencies, and should be accessible the next time you run R.