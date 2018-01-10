## Intro
This is intended to be a default set of procedures for Weecologists to collaborate together using a Git/GitHub repository. For projects that are primarily being worked on by one person, this is probably unnecessary, but you may want to follow this anyway, so as to ingrain the workflow practices.

## Setup
*If you haven't done so already, please check out the onboarding [section with links to Git and Github resources](https://github.com/weecology/lab-wiki/wiki/New-Lab-Member-Onboarding-Guide#git-and-github).*

In this guide, we presume that there is a single repo on GitHub and multiple users, who work on clones of that repo (on their local machines), and interface through GitHub.

## Branching

By default, git repos have a `master` branch. If you are working in a repo and use commits to track the iterative versions of the project, then you're working on this branch.

You can see the branches in your project using `git branch` from the command line while in the folder with a git repo. This will list the branches in the repo, with the current version of the repo indicated with an asterisk (and possibly a different color):
```bash
> git branch
```
```
  biomass-function
  hao-data-vignette
* master
```


## Pull Requests / Merges