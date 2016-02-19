1. [Request an account](http://www.rc.ufl.edu/help/account-request/)

2. connect to the server with `ssh <YOUR_USERNAME>@gator.hpc.ufl.edu` from the Unix terminal or a Windows SSH client ([more info here](http://wiki.hpc.ufl.edu/doc/Getting_Started)). Enter your password when prompted.

3. This will take you to a Unix terminal on the login server.  This is where you can upload files and start larger jobs on other servers. You're not supposed to run big computations on this server. Often, the easiest way to transfer files is using `git clone`; you can also use other methods, including FTP or `scp`. [More information about storage](https://www.rc.ufl.edu/about/policies/storage/)

4. You can start a job using a file like the one below (based on a file from Shawn, updated by Dave)

5. You can check on your job's status at rc.ufl.edu/jobstatus/


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
#PBS -l nodes=1:ppn=N_NODES

#The amount of memory that your script will require. This can be just a rough guess with some buffer added on.
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