We have a lab server which is fairly powerful. It has 32GB of RAM and a 2 core Intel Xeon processor. This is faster and has more ram than any of our laptops. It's good for doing things that may take too long on a desktop/laptop or as a test bed for running on the hipergator.  

Note you must be on campus to use serenity, or logged in via the VPN. 

# Using RStudio
Open a browser and go to http://serenity.ifas.ufl.edu:8787 and login with your serenity username and password. Note this will only work when on campus. For off campus access see below.  
This runs exactly like RStudio on your desktop. You'll have to re-install any packages that you need.
This works great for code that takes a long time to run. You can start something, then close the browser and Rstudio will keep running on serenity. 

## Logging in from off campus
There are two options to login from off campus. The first is to use the UFL VPN. Once connected you can go to the address above. The second is to access it via the hipergator login node using the steps below.

### On Windows  
Download the putty ssh client [here](https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe).

Open putty and make a connection to the hipergator login node. Put `hpg.rc.ufl.edu` into the Host Name box. Put `hipergator` into the Saved Sessions box and click Save to save this setup. Then in the menu go to Connection -> SSH -> Auth -> Tunnels. Put `8787` in the source port and `serenity.ifas.ufl.edu:8787` in the Destination and click add. 

![](https://i.imgur.com/gEtmuCn.png)

Then in the left side go back to the Session tab and click Save again. Then click open to connect. Enter your username and password. Once connected open a browser and go to http://localhost:8787

### On mac or linux  
SSH to the hipergator using the following command   

`ssh <username>@hpg.rc.ufl.edu -L 8787:serenity.ifas.ufl.edu:8787`

Once logged in open a browser and go to http://localhost:8787


## Getting a login
Ask Shawn or Henry for a username and initial password