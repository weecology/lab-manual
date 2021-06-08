---
title: "Collaborating Using Git & GitHub"
linkTitle: "Git - Collaboration"
---

## Intro
This is intended to be a default set of procedures for Weecologists to collaborate together using a Git/GitHub repository. For projects that are primarily being worked on by one person, this is probably unnecessary, but you may want to follow this anyway, so as to ingrain the workflow practices.

## Setup
*If you haven't done so already, please check out the onboarding [section with links to Git and Github resources](https://github.com/weecology/lab-wiki/wiki/WEecology:-New-Lab-Member-Onboarding#git-and-github).*

In this guide, we presume that there is a single repo on GitHub and multiple users, who work on clones of that repo (on their local machines), and interface through GitHub.

## Branching

One way of thinking about git branches is that each branch represents a "lineage" of commits in a repo. By default, git repos have a `master` branch, and adding commits to a new repo will create iterative versions of the project, all considered to be part of the `master` branch.

You can see the branches in your project using `git branch` from the command line while in the folder with a git repo. This will list the branches in the repo:
```bash
~/projects/portalr > git branch
```
```
  biomass-function
  hao-data-vignette
* master
```

Here, `master` is marked with an asterisk (and possibly a different color) to indicate that it is the "active" branch. What this means is that new commits added to the repo will be derived from the end of the master branch and included as part of that branch.

### Making New Branches

We can create new branches by specifying a new branch name when using the `git branch` command. This allows us to start a new "lineage" of commits from the current state of the repo.
```bash
~/projects/portalr > git branch hao-test-branch
```
When we look at the branches, we now see:
```bash
~/projects/portalr > git branch
```
```
  biomass-function
  hao-data-vignette
  hao-test-branch
* master
```

Notice that the active branch is still "master".

### Switching Branches

To change the active branch, we use the `git checkout` command:
```bash
~/projects/portalr > git checkout hao-test-branch
```
```
Switched to branch 'hao-test-branch'
```

This is what it looks like when we run `git branch` afterword:
```bash
~/projects/portalr > git branch
```
```
  biomass-function
  hao-data-vignette
* hao-test-branch
  master
```

### Pushing to GitHub

After we have created a branch on our local clone of the repo, and made some commits, we might want to push those commits to GitHub. The first time we do so, however, we encounter an error:
```bash
~/projects/portalr > git push
```
```
fatal: The current branch hao-test-branch has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin hao-test-branch
```

The reason for this error is that the repo on GitHub does not have the branch `hao-test-branch`, and commits have to be assigned to a branch. The suggested command does several things at once:
1. create a branch called `hao-test-branch` on the GitHub repo (which has the remote name `origin`)
2. establish a link between the local branch called `hao-test-branch` and the GitHub branch called `hao-test-branch`
3. push the local commits on `hao-test-branch` to GitHub.

### Pulling from GitHub

Suppose someone starts making an update and has pushed it to GitHub and wants your help before merging it into the master branch. How do you download that new branch?

First, make sure we get all the information from the GitHub repo. This assumes that the GitHub repo is named as the "origin" remote (which is the default).
```bash
~/projects/portalr > git fetch origin
```

We can then view the possible branches using
```bash
~/projects/portalr > git branch -r
```
```
  origin/biomass-function
  origin/fix-test
  origin/hao-data-vignette
  origin/hao-export-obs-func
  origin/hao-loadData-update
  origin/hao-reorder-args-remove-incomplete-censuses
  origin/master
  origin/namespace_issue
  origin/namespaceissues
  origin/standardize_column_names
```

We want to create a local branch to mirror the "fix-test" branch:
```bash
~/projects/portalr > git checkout -b fix-test origin/fix-test
```
```
Branch fix-test set up to track remote branch fix-test from origin.
Switched to a new branch 'fix-test'
```

This has done several things: it retrieved the branch from GitHub to our local machine, set up tracking, and changed the current active branch. Now, if we make new commits to the local copy of the branch, we are able to push directly to that corresponding branch on GitHub.

## Pull Requests

The preference is to use GitHub to merge the updates on a new branch back into `master`. We can do this by going to the "Pull requests" tab on the GitHub repo page and creating a "New pull request".
![](https://github.com/weecology/lab-wiki/blob/master/github_PR_tab.png)

Suppose we want to merge from `hao-test-branch` into `master`. Then we select `master` as the "base: " branch, and `hao-test-branch` as the "compare: " branch. We can then write some comments for our new pull request before clicking on "Create new pull request".

*If the pull request fixes an issue, you can include keywords to [automagically close](https://help.github.com/articles/closing-issues-using-keywords/) the issue when the pull request is merged.*

### Updating Pull Requests

At this point, other people can comment on the pull request itself in GitHub, if discussion regarding the changes needs to occur.

Additionally, assuming that the pull request has not yet been merged, further commits *to that branch on GitHub* are automatically included with the pull request. Thus, if you later find a bug, you can make further changes and not have to submit a new pull request.

### Merging Pull Requests

In general, check with one of the repo maintainers about merging pull requests. This ensures that the `master` branch doesn't break (too often) and that everyone is informed about changes.

## Summary Example

Objective: I want to fix issue #1 in the https://github.com/weecology/portalr repo.
1. Download the repo from GitHub and onto my local machine. [`git clone`]
2. In my local machine, create a new branch (e.g. `hao-add-biomass-function` <- prefacing the branch name with your name helps prevent branch name collisions. [`git branch`]
3. Switch to the new branch. [`git checkout`]
4. Make the updates on my local machine. [`git commit`]
5. Push the updates to GitHub. [`git push`]
6. Create the pull request on GitHub. [GitHub web interface]
7. Merge the pull request on GitHub. [GitHub web interface]
8. On my local machine, switch back to the master branch. [`git branch`]
9. Get the updates to the master branch [`git pull`]
(optionally) Delete the branch on GitHub. [GitHub web interface, "Code" tab, "## branches"]
(optionally) Delete the branch on my local machine. [`git branch -d hao-add-biomass-function`]




