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

Resources: [Software Carpentry] (http://swcarpentry.github.io/git-novice/), [Jenny Bryan's course website](http://stat545-ubc.github.io/git00_index.html)

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

4. In this page, name the repo, preferably something short and succinct that uniquely describes the project. 

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

Adding files, pushing and pulling:

