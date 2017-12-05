# Starting a tensorflow session and a jupyter notebook

This script will start a jupyter notebook on the hipergator. The details of how to connect will change each time, so instructions for connecting will be saved to `jupyter.log`.

The instructions will include a command to type from your local machine, which will look like:

`ssh -NL 8080:XXXX.ufhpc:XXXX YOUR_USERNAMEd@hpg2.rc.ufl.edu`

This says, "connect port 8080 on my computer to a specific port on a specific hipergator machine." Thus, visiting `http://localhost:8080` in your browser will connect you to the jupyter notebook.

```
#!/bin/bash
#SBATCH --job-name=jupyter
#SBATCH --output=jupyter.log
#SBATCH --nodes=1
#SBATCH --ntasks=16
#SBATCH --mem=2gb
#SBATCH --time=12:00:00
#SBATCH --qos=ewhite
date;hostname;pwd

ml tensorflow
port=$(shuf -i 20000-30000 -n 1)
 
echo -e "\nStarting Jupyter Notebook on port ${port} on the $(hostname) server."
echo -e "\nSSH tunnel command: ssh -NL 8080:$(hostname):${port} ${USER}@hpg2.rc.ufl.edu"
echo -e "\nLocal URI: http://localhost:8080"
export LD_LIBRARY_PATH=/usr/local/cuda/extras/CUPTI/lib64:$LD_LIBRARY_PATH
launch_tensorflow jupyter-notebook --no-browser --port=${port} --ip='*'

jupyter notebook list
 
date
```

For convenience, you can run the following script to start the hipergator job and automatically print out the log file with the instructions for connecting.

```
#!/bin/bash

rm jupyter.log
touch jupyter.log
sbatch jupyter.job

tail -f jupyter.log
```


# Tensorboard

To launch tensorboard on the server, either start a job with the following commands or type them into a development session:

`ml tensorflow`

`launch_tensorflow tensorboard --logdir=XXXX/`

Tensorboard will print something like the following in your terminal: `http://dev2.ufhpc:6006`

From a local terminal, type `ssh -NL 8000:URL_AFTER_HTTP harris.d@hpg2.rc.ufl.edu`, where `URL_AFTER_HTTP` will look something like `dev2.ufhpc:6006`, depending on what was printed above.

Then send your browser to `http://localhost:8000/`
