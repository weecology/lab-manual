---
title: "Using Git From RStudio"
linkTitle: "RStudio + Git"
---

Just a brief introduction on how to easily set up a Git/GitHub repo in RStudio:
   * Make sure Git is set up on your computer and in R (ask Ethan for help on this one)
   * Sign into your GitHub account 
   * Click on the plus sign in the top right-hand corner (near your profile picture) and select "New repository". You can    choose to make your new repo through your account or the Weecology one on the next page.
   * Name your repository, add a quick description if desired, select Public or Private (most often Public) and _be sure to check the box to initialize a README document_. Click _Create Repository._
   * You'll now be on the page for your new repo. Find the green icon **CODE** that has either an https address or something that looks like an email address (SSH). Make sure that the box to the left of text box says HTTPS rather than SSH. Then click the clipboard icon to the right of the text box. This will copy that address to your clipboard.
   * Now you're done with GitHub. Open up RStudio. Go to _File_ and select _New Project_. If Git is properly set up in RStudio, you should have an option called _Version Control_. Click on that option.
   * Select the _Git_ option from the next menu.
   * Paste the HTTPS address into the _Repository URL_ box. It will auto-fill the _Project directory name_. Make sure the project is being created in the appropriate folder.
   * Click _Create Project_ and voila!
   * Now you should see a _Git_ tab next to the _Environment_ and _History_ tabs. From there, you can make commits, push (green up arrow), and pull (blue down arrow).