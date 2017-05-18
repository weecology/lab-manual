We have a lab server which is fairly powerful. It has 32GB of RAM and a 2 core Intel Xeon processor. This is faster and has more ram than any of our laptops. It's good for doing things that may take too long on a desktop/laptop or as a test bed for running on the hipergator.  

Note you must be on campus to use serenity, or logged in via the VPN. 

### Getting a login
Ask Shawn or Henry for a username and initial password

### Logging in via ssh

Open a terminal (or a git bash window) and type

ssh username@serenity.ifas.ufl.edu

From here you can move to different folders in your home directory to run git commands, or clone a repo from github.  

### Using Rstudio
Open a browser and go to http://serenity.ifas.ufl.edu:8787 and login with your serenity username and password  
This runs exactly like Rstudio on your desktop. You'll have to re-install any packages that you need.
This works great for code that takes a long time to run. You can start something, then close the browser and Rstudio will keep running on serenity. 
