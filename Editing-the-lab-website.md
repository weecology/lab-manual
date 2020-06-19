# Clone the Website repo
The website is up on github. To edit it you will need to put a local copy of the website on your computer first. Clone the [website repo](https://github.com/weecology/website)

# One time setup
* Install the `blogdown` R package
* Run: `blogdown::install_hugo()`
* Create a new R project in your local copy of the website repository

# Viewing your changes before pushing back online
To see if your changes are working, you can things up do you see a live updating copy of the website on your local computer. You can do this before you make changes or after, but check to make sure the site builds before you push your edits back up. (Morgan forgot this step once and it was....unfortunate). 
* Open the R project
* Run `blogdown::serve_site()`

* The site will now show in a pane in RStudio, to see it in your browser click the `Show in new window` button
* The site should "live update" as you save files. It may take a few seconds to update.

# Push back to the website repo
Once you push your commits, the website should rebuild. This might take a few minutes, so give it a little time before you panic.