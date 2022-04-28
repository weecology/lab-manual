---
title: New member onboarding
type: book
---

# Intro

This guide is a general reference for being in the Weecology lab at UF. Some info is below, but much of it is actually located among the various lab-wiki pages, and linked to from here.

## How to Use

If you are a new member to the lab, please see the [issues](https://github.com/weecology/lab-wiki/issues) page of the lab wiki for the onboarding checklist. Make a new issue with your name and copy the list, and then be sure to go through it, referring back to the info here as necessary.

# General Lab Policies

## Lab Philosophy
See [Way of Weecology](https://github.com/weecology/lab-wiki/wiki/Way-of-Weecology).

## Lab Code of Conduct
See [here](https://github.com/weecology/lab-wiki/wiki/Code-of-Conduct).

## Software Project Code of Conduct
For software projects, repos should adopt a separate code of conduct for interactions with contributors. See [here](https://github.com/weecology/lab-wiki/wiki/Software-Project-Code-of-Conduct) for an example.

## Tea
Earl grey should almost always have milk in it! (though this is technically optional, per ISO 3103)

## Expectations / Annual Self-Assessment

See [here](https://github.com/weecology/lab-wiki/wiki/Annual-self-assessment) for more info.

## Slack and GitHub

- [ ] Markdown formatting
- [ ] Look through and subscribe to channels on Slack
- [ ] Basic commands in Slack (replies, responses, reminders, notifications for individuals/channel)
- [ ] GitHub repos (creating, subscribing, making issues, pull requests)
- [ ] Lab policies around using GitHub

## Calendars

Once you have your weecology.org Google account, you will have access to the lab calendars. You can access these from a web browser at [https://calendar.google.com/](https://calendar.google.com/). (**Note that you may need to use the account management button in the upper-right corner if you are logged in with other Google accounts at the same time.**)

Please keep your personal calendar up to date on when you will be out of town to help with scheduling meetings. Ethan & Morgan will have viewing access to your calendar. Some calendars you might want to add to your view to stay informed are:
* "ethan" (Ethan White)
* "morgan" (Morgan Ernest)
* "conference room"

The conference room schedule is maintained separately. You might need to contact someone who already has access to share the calendar with you.

## Lab Meeting

(for Spring 2018) Weds at 1pm ET.

Typical agenda is something like:
* general announcements
* short summary of past week from individuals present
* presentation of research (see [here](https://github.com/weecology/lab-wiki/wiki/Lab-Meeting) for the schedule)

## Contact Info

[Emergency Contact Info here](https://github.com/weecology/lab-wiki/wiki/Emergency-contact-information)

For correspondence, you can use the [WEC office contact info](https://wec.ifas.ufl.edu/about-wec/contact-information/).

# Day-to-Day Operations

## Computer Setup

Tell Glenda if you need a new computer.

Here's a basic checklist for computer privacy and security. For more info, check out the wiki page on [Computer Security and Privacy Resources](https://github.com/weecology/lab-wiki/wiki/Computer-Security-&-Privacy-Resources)

- [ ] Get a password manager for your various website passwords.
- [ ] Set up 2FA where you can, and especially for important services like email and GitHub
- [ ] ^ Talk to Ethan or Glenda about getting a Yubikey for 2FA if you don't have one already
- [ ] Set up a SSH key for command-line access to GitHub. [instructions here](https://help.github.com/articles/about-ssh/)

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
* Olivia Guest’s [cheatsheet](http://neuroplausible.com/github)
* Alice Bartlett's [slides on "Git for humans"](https://speakerdeck.com/alicebartlett/git-for-humans) <- *Hao recommends this as a top-level description of what Git is all about*
* Chris Beams's [blogpost on writing commit messages](https://chris.beams.io/posts/git-commit/)
* Software Carpentry [Git lesson](https://swcarpentry.github.io/git-novice/)
* Jenny Bryan's book, ["Happy Git and GitHub for the useR"](http://happygitwithr.com/), book for UBC Stat 545
* David Winterbottom's [blogpost on branches and pull request workflow](http://codeinthehole.com/tips/pull-requests-and-other-good-practices-for-teams-using-github/)

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

The lab printer is located in room 015 and accessible from the UFL network at `10.242.89.51`. You may need to [download and install drivers](https://support.hp.com/us-en/drivers/selfservice/hp-color-laserjet-pro-mfp-m478-m479-series/19202514/model/19202521) before adding it as a printer in order for it to function properly.

### Shared Spaces

[Learn about lab spaces and how to use them](/docs/lab-policy-procedures/lab-space)

# Campus Resources

## UFL Police / Security

## Student Health Care Center

Located in the historic Infirmary Building on Fletcher Drive. [more info](http://shcc.ufl.edu/)
* Health Insurance:
  - Grad students can apply to GatorGradCare Helath insurance. Despite it is free, enrollment is not automatic: you need to request for renew it every year by mid September [here](https://bluebiz.bcbsfl.com/stuenroll/GatorGradCare.do). If you are interested in knowing more about GatorGrad Care benefits, see [here](https://benefits.hr.ufl.edu/health/gatorgradcare/)
* Dental:
  - Students enrolled in GatorGradCare are eligible for a complete oral health exam and cleaning once a year. Here is  a [brochure](https://benefits.hr.ufl.edu/wp-content/uploads/sites/3/2018/05/GradDentalBenefits.pdf) of what it is about!
* vision?
* Mental Health:
  - Gradschool (and Academia) is awesome but stressful: fortunately UFL aknowledges it, and it has some resources available for us. Everybody may need them, and using these resources can make a difference to manage strees, help with focusing and productivity, and most importantly, help everybody to take care of their mental health. If you are interested to learn more here is a list of some available resources.
  - Staff have access to UF's [Employee Assistance Program](http://eap.ufl.edu).
  - University of Florida Counseling and Wellness Center (CWC) https://counseling.ufl.edu/ : If a student has an urgent mental health need during business hours, CWC counselors are available between the hours of 9am and 4pm, Monday through Friday at Radio Road or the 4th floor of Peabody Hall. If a student has an urgent mental health need after business hours, phone consultation with a counselor is available 24 hours a day, 7 days a week. Call at 352-392-1575. 3190 Radio Road, Gainesville, FL 32611 Monday-Friday 8am-5pm 352-392-1575
  - https://umatter.ufl.edu/ Emergency consultations are available with the CARE Team anytime, including outside of business hours. CARE Team: Peabody Hall, 3rd Level Monday - Friday, 8:00 am - 5:00 pm 352-294-CARE (2273) umatter@ufl.edu
  - University of Florida Student Health Care Center (https://shcc.ufl.edu/) 280 Fletcher Drive Gainesville, Monday - Friday, 8:00 am - 5:00 pm; Closed Saturdays; Sunday, 12 - 4:00 pm 352-392-1161
  - GatorWell Health Promotion Services (https://gatorwell.ufsa.ufl.edu/​​​​​​​): Reitz Union, Suite 1100 Monday - Friday, 8:00 am - 5:00 pm 352-273-4450 GatorWell@ufsa.ufl.edu

* Other resources:
  - National Sexual Assault Online Hotline
Website: https://ohl.rainn.org/online/ 
  - PsyberGuide resource: Mental Health Product Guide (www.psyberguide.org) A non-profit website providing reviews of mental health apps. Their goal is to provide reviews of mental health apps that are free of preference, bias, or endorsement. 
  - Student Success (e.unisa.edu.au/enrol/advself/item.php?enrolid=129)
Student Success is a program to help students be successful at school, and as future professionals. It covers self-care, problem-solving, and self-management.
  - thedesk (www.thedesk.org.au/)
Online resource that aims to normalize experiences and help students to develop skills to be able to get things done, stay connected with others, manage stress and worries, and improve health.

## Legal Services

* [UF Student Legal Services](https://www.studentlegalservices.ufl.edu/)
* 

## Networking

* Zoocial! 
  - Every Friday night grad students mainly from WEC, Biology, and Acquatic Sciences meet at 5:00 PM outside Bartram Hall. It is a relaxed, puppy friendly opportunity to meet other folks. 


## WEC IT

* point of contact: Tom Barnash (see http://www.wec.ufl.edu/people/staff.php)

## Financial Services

## Travel

See https://github.com/weecology/lab-wiki/wiki/UF-Travel-Guidelines for info about travel and reimbursement.

## Grad Student Union / Association?

## Buying Stuff

See https://github.com/weecology/lab-wiki/wiki/PCARDS for info on setting up a PCARD.

## Poster

See [here](https://github.com/weecology/lab-wiki/wiki/Making-a-Poster) for more info.

## Florida Residency (for students)

You'll be required to apply for Florida Residency after your first year. To make it as smooth as possible follow the steps in the [residency notes](https://github.com/weecology/lab-wiki/wiki/Florida-Residency) **before your first day of classes**. 

## Florida Driver's License and Car Registration

Students generally do not need to do this, but employees are supposed to register cars within 10 days (!), which first requires a FL driver's license... *Do pay close attention to the ID requirements.*

See [here](http://www.flhsmv.gov/dhsmv/newflres.html) for more info.