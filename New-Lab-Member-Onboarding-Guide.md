# Intro

This guide is a general reference for being in the Weecology lab at UF. Some info is below, but much of it is actually located among the various lab-wiki pages, and linked to from here.

## How to Use

If you are a new member to the lab, please see the [issues](https://github.com/weecology/lab-wiki/issues) page of the lab wiki for the onboarding checklist. Make a new issue with your name and copy the list, and then be sure to go through it, referring back to the info here as necessary.

# General Lab Policies

## Lab Philosophy
***TODO: fill out***

## Lab Code of Conduct
See [here](https://github.com/weecology/lab-wiki/wiki/Code-of-Conduct).

## Software Project Code of Conduct
For software projects, repos should adopt a separate code of conduct for interactions with contributors. See [here](https://github.com/weecology/lab-wiki/wiki/Software-Project-Code-of-Conduct) for an example.

## Expectations / Annual Self-Assessment

See [here](https://github.com/weecology/lab-wiki/wiki/Annual-self-assessment) for more info.

## Calendars

Once you have your weecology.org Google account, you will have access to the lab calendars. You can access these from a web browser at [https://calendar.google.com/](https://calendar.google.com/). (**Note that you may need to use the account management button in the upper-right corner if you are logged in with other Google accounts at the same time.**)

Please keep your personal calendar up to date on when you will be out of town to help with scheduling meetings. Ethan & Morgan will have viewing access to your calendar. Some calendars you might want to add to your view to stay informed are:
* "ethan" (Ethan White)
* "morgan" (Morgan Ernest)

The conference room schedule is maintained separately. You might need to contact someone who already has access to share the calendar with you.

## Lab Meeting

(for Fall 2017) Mondays at Noon

Typical agenda is something like:
* general announcements
* short summary of past week from individuals present
* presentation of research (see [here](https://github.com/weecology/lab-wiki/wiki/Lab-Meeting) for the schedule)

## Contact Info

[Emergency Contact Info here](https://github.com/weecology/lab-wiki/wiki/Emergency-contact-information)

***TODO: General mailing address / phone number / fax number for the lab?***

# Day-to-Day Operations

## Computer Setup

### Basic Software Setup

[Programming setup for Macs](https://github.com/weecology/lab-wiki/wiki/Computer-Setup-for-Mac)

***TODO: Complete existing page***

***TODO: Info for other OSes***

The lab is transitioning to use of [Zotero](https://www.zotero.org/) as a common standard for managing bibliographies.

### Programming

* Style Guidelines

  For Python, the [PEP 8 Style Guide](https://www.python.org/dev/peps/pep-0008/).

  For R, [Hadley Wickham's Style Guide](http://adv-r.had.co.nz/Style.html).

  For R packages, check out [rOpenSci's onboarding guide](https://github.com/ropensci/onboarding/blob/master/packaging_guide.md)

Lab wiki pages:
* [parallelization in R](https://github.com/weecology/lab-wiki/wiki/Parallelization-in-R)

### Git and GitHub

Some external resources:
* Alice Bartlett's [slides on "Git for humans"](https://speakerdeck.com/alicebartlett/git-for-humans) <- *Hao recommends this as a top-level description of what Git is all about*
* Chris Beams's [blogpost on writing commit messages](https://chris.beams.io/posts/git-commit/)
* Software Carpentry [Git lesson](https://swcarpentry.github.io/git-novice/)
* Jenny Bryan's book, ["Happy Git and GitHub for the useR"](http://happygitwithr.com/), book for UBC Stat 545
* David Winterbottom's [blogpost on branches and bull request workflow](http://codeinthehole.com/tips/pull-requests-and-other-good-practices-for-teams-using-github/)

(Hao) I have this in my `~/.gitconfig` file to enable the `git lg` alias on command-line.
```
[alias]
lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%<(40,trunc)%s%C(reset) %C(reverse white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
lg = !"git lg1"
```

Lab wiki pages:
* [setting up new GitHub repos and linking with RStudio](https://github.com/weecology/lab-wiki/wiki/GitHub-Repos-in-RStudio)
* [using branches in Git/GitHub for collaboration](https://github.com/weecology/lab-wiki/wiki/Git-guide-to-collaborative-workflows)

### Backup

Offsite backup of lab computers is best done using the *T: drive*. [Access instructions](https://github.com/weecology/lab-wiki/wiki/Accessing-the-T:-drive)

***TODO: Info on how to setup automated backups? ***

### Lab Printer

The lab printer is located in room 015 and accessible from the UFL network at `10.242.89.254`. You may need to [download and install drivers](http://www.dell.com/support/home/us/en/04/product-support/product/dell-c3760dn/drivers) before adding it as a printer in order for it to function properly.

# Campus Resources

## UFL Police / Security

## Student Health Care Center

Located in the historic Infirmary Building on Fletcher Drive. [more info](http://shcc.ufl.edu/)
* dental?
* vision?
* mental health?
  - staff have access to UF's [Employee Assistance Program](http://eap.ufl.edu/)

## Legal Services

* [UF Student Legal Services](https://www.studentlegalservices.ufl.edu/)
* 

## WEC IT

* point of contact: Tom Barnash (see http://www.wec.ufl.edu/people/staff.php)

## Financial Services

## Travel

## Grad Student Union / Association?

## Buying Stuff

See [here](https://github.com/weecology/lab-wiki/wiki/PCARDS) for info on setting up a PCARD.

## Poster

See [here](https://github.com/weecology/lab-wiki/wiki/Making-a-Poster) for more info.

## Florida Residency (for students)

See [here](https://github.com/weecology/lab-wiki/wiki/Florida-Residency) for more info.

## Florida Driver's License and Car Registration

Students generally do not need to do this, but employees are supposed to register cars within 10 days (!), which first requires a FL driver's license... *Do pay close attention to the ID requirements.*

See [here](http://www.flhsmv.gov/dhsmv/newflres.html) for more info.
