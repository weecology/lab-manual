**Terminal**

This is an application on Macs. It is opened by double-clicking on the icon, which should bring up a small window with a black background. The Terminal is used to move around in the file directory, rearrange files, and use git. 

**Python**

_IDE_

_Packages_

_Projects_

_Links to get started coding in Python_

_Using git/GitHub_


**R**

_Installing R_

_Installing RStudio_

_Packages_

_Projects_

_Using git/GitHub_


**Dependencies**



**Git/GitHub**

Resources: [Software Carpentry] (http://swcarpentry.github.io/git-novice/), [Jenny Bryan's course website](http://stat545-ubc.github.io/git00_index.html), [Roger Dudler cheatsheet] (http://rogerdudler.github.io/git-guide/) 

_Installing git_

1. Open up the Terminal, type in "git" and press enter.

2. This should cause a pop-up window to appear. It will have several options; click on "Install" (not "Get Xcode", see "Installing Xcode" for that). 

3. Click "Agree". 

4. When the install is finished, click "Done". 

5. To make sure this worked, type in "git" in the Terminal and press enter. Some information will come up, including a list of common commands. 

_Installing Xcode_

_GitHub_

Create a GitHub account by going to https://github.com/ 

This is a service that allows you to store your code, project management materials, etc., online. It allows for other people to look at your work (if the repo is public). It also saves all the versions of your code as you change it, which is referred to as version control. This eliminates the need for creating multiple copies of code as you change it (e.g., folder with files called "data_analysis", "data_analysis_3", "data_analysis_45", "data_analysis_final", and "data_analysis_final_really") and you can use the online GitHub interface to easily look back at previous versions of your code and see what was changed. 

_Repositories_

A repository is where you put all of the materials related to single project. One repository per project. 

Creating a GitHub repository:

1. Open up a browser, go to the GitHub website, and sign into your GitHub account. Navigate to your profile page.

2. Click on the "Repositories" tab in the top middle of the page. 

3. In the upper right hand corner, click on the green "New" button. 

4. In this page, name the repo, preferably something short and succinct that uniquely describes the project. Also, there should be no spaces in repository names. If the name consists of multiple words, separate them by an underscore, dash, or camel case, e.g., mammal_community_dynamics, mammal-community-dynamics, MammalCommunityDynamics. 

5. Select if the repo will be public or private. Keep in mind that you have a limited number of private repos for free, so most of your repos will likely be public. Having your research publicly available also makes for better science. 

6. Check "Initialize this repository with a README". 

7. Leave both "Add .gitignore" and "Add a license" as "None". 

8. Click green "Create repository" button. You've created your new repository, congrats! 

Cloning GitHub repository: 

The repository that was created above is the remote repository. This can be accessed from any computer using the browser. You also need to create a copy of the remote repository called the local repository. This copy of the repo can only be accessed from the computer it is created on. You will do work (e.g., changing code) on the local repo. 

1. In the browser, navigate to the main page of the repository you want to clone. 

2. In the right-hand column near the bottom, there is a bar containing a URL. There are two possible options for this URL, either HTTPS or SSH. You can switch between these two by clicking on the relevant blue hyperlinked acronym below the URL. 

3. Click on the HTTPS blue hyperlinked word. Either HTTPS or SSH can be used, but it is easier to start with HTTPS. The difference between these is how they link the local repo to the remote, but that difference is not important right now. 

4. Copy the HTTPS URL. 

5. Open up the Terminal and navigate to the location on your computer where you want the local repo to be located. You can navigate around using the commands "ls" (this displays all the folders and files in the current directory) and "cd". This latter command changes the directory, so you will type in the path for the directory you want to go to. For example, if I want to put the repo in the folder Projects, which is within the folder Documents, I would type the following into the Terminal: "cd Documents/Projects". Then hit enter. 

6. Once you're in the directory where you want the repo to be located, type in the command "git clone", a space, and then paste in the HTTPS URL. 

7. Hit enter. This should create a new folder in the chosen directory that has the same name as the remote repo. This is your local repository. 

Adding files and commits to local repository: 

An important aspect of git/GitHub is version control. As you change scripts, you can use git to save all the different versions of scripts and then use GitHub later on to easily look at each of these versions. Then, if you mess up your code or don't like the direction it's heading in, you can access and use a previous version of your script very easily. 

The way that you save these versions using git is by doing something called a commit. Each commit represents a different version of a script. Because you choose when to do a commit, you get to choose how different all of the versions of the script are. You should definitely make a commit for every major change in the code that you make, but you can never commit too often. When in doubt, commit. 

Another important, and confusing, step in this process is adding the script. Before you can commit the newest version of a script, you have to add that script to the stage. This means that if you've changed several of the scripts within one local repository, you can add all of these scripts to the stage and commit them together, or you can add one script to the stage and commit it at a time. 

1. Create a new script (in Python, R, or whatever language) and save the script in the folder for the local repository you've just created. Similar to the names of repositories, there should be no spaces in script names. See the fourth bullet point in the "Creating a GitHub Repository" section for naming conventions. 

2. If you are not already there, open up the Terminal and navigate to the local repository folder using the "cd" command. 

3. To add the script, type in "git add " and then the name of the script, and then hit enter. (There should be a space between the add command and the script name). The script is now on the stage. Optional: You can repeat this multiple times in a row with different script names if you're adding multiple scripts to the stage at the same time.

4. To make sure that the script has been added, type in "git status" and hit Enter. This will bring up information about the repo that you are currently looking at. If you've correctly added the script, under the "Changes to be committed:" header, there should be an indented bit of text that will be formatted as "modified: " and the name of the script you've added.  

5. Now you want to commit this version of the script. In the Terminal, type in "git commit -m "_message_" and hit enter. The _message_ is where you will insert a succinct, informative description of what changed between the last version and this newest version of the script. Writing good commit messages is a bit of an art, but there is some information [here] (http://chris.beams.io/posts/git-commit/) on good commit messages. 

6. You can use git status again to check that the commit worked. Type in "git status" and hit Enter. Now the entire "Changes to be committed:" section should be gone, because there should no longer be any changes that haven't been committed in this repo. 

7. You can look at this commit, and all previous commits, by typing in "git log" and hitting Enter. This will bring up a list of the commits, with the most recent commit at the top. The information about each commit includes the author, date, and message of the commit. At the top of each commit, there is a long string of letters and numbers. This is the hash, or unique identifier, for each commit. 

8. You will do this add and commit workflow (steps 2-7) each time you make a substantial change to this script, or when you want to add another script. 

Pushing and pulling:

TODO: add summary here (about getting changes up to GitHub repository)
