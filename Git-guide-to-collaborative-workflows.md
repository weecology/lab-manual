## Intro
This is intended to be a default set of procedures for Weecologists to collaborate together using a Git/GitHub repository. For projects that are primarily being worked on by one person, this is probably unnecessary, but you may want to follow this anyway, so as to ingrain the workflow practices.

## Setup
*If you haven't done so already, please check out the onboarding [section with links to Git and Github resources](https://github.com/weecology/lab-wiki/wiki/New-Lab-Member-Onboarding-Guide#git-and-github).*

In this guide, we presume that there is a single repo on GitHub and multiple users, who work on clones of that repo (on their local machines), and interface through GitHub.

## Branching

One way of thinking about git branches is that each branch represents a "lineage" of commits in a repo. By default, git repos have a `master` branch, and adding commits to a new repo will create iterative versions of the project, all considered to be part of the `master` branch.

You can see the branches in your project using `git branch` from the command line while in the folder with a git repo. This will list the branches in the repo:
```bash
~/projects/demo > git branch
```
```
* master
```

Here, `master` is marked with an asterisk (and possibly a different color) to indicate that it is the "active" branch. What this means is that new commits added to the repo will be derived from the end of the master branch and included as part of that branch.

### Making New Branches

We can create new branches by specifying a new branch name when using the `git branch` command. This allows us to start a new "lineage" of commits from the current state of the repo.
```bash
~/projects/demo > git branch dev
```
When we look at the branches, we now see:
```bash
~/projects/demo > git branch
```
```
  dev
* master
```

Notice that the active branch is still "master".

### Switching Branches

To change the active branch, we use the `git checkout` command:
```bash
~/projects/demo > git checkout dev
```
```
Switched to branch 'dev'
```

This is what it looks like when we run `git branch` afterword:
```bash
~/projects/demo > git branch
```
```
* dev
  master
```

### Pushing to GitHub

After we have created a branch on our local clone of the repo, and made some commits, we might want to push those commits to GitHub. The first time we do so, however, we encounter an error:
```bash
~/projects/demo > git push
```
```
fatal: The current branch dev has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev
```

The reason for this error is that the repo on GitHub does not have the branch `dev`, and commits have to be assigned to a branch. The suggested command does several things at once:
1. create a branch called `dev` on the GitHub repo (which has the remote name `origin`)
2. establish a link between the local branch called `dev` and the GitHub branch called `dev`
3. push the local commits on `dev` to GitHub.

### Pull Requests

The preference is to use GitHub to merge the updates on a new branch back into `master`. We can do this by going to the "Pull requests" tab on the GitHub repo page:
![](https://github.com/weecology/lab-wiki/blob/master/github_PR_tab.png)


