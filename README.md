# default-R

R has features to allow you to customize the start-up protocols. These are often used to automatically load packages or custom functions that you use regularly, or to change default settings. These settings can be saved in a Rprofile.site file that is saved in your R directory.

For some examples, check out:

http://www.statmethods.net/interface/customizing.html

https://www.r-bloggers.com/fun-with-rprofile-and-customizing-r-startup/




## Your Rprofile.site File

After creating your profile script, you need to add it to your R program directory.

In the Windows environment you can usually add your Rprofile.site file to your R directory at:

C:\Program Files\R\R-3.3.1\etc



## Sourcing External Functions

The Rprofile.site script includes a function called `.First`. R will automatically run this function on start-up. 

This is a good place to load packages that you regularly use. You can also use it to source an external script. 

I have started placing my preferred customization steps into a script on GitHub, as it is easy to update and maintain, and I can retain the same user experience across many different computers. I have included a line to source this script in the `.First` function. This links to the `source-me.R` script in this repository.

```r
.First <- function(){
 library( dplyr )
 source( "https://raw.githubusercontent.com/lecy/Rprofile/master/source-me.R" )
}
```



## Example Rprofile.site Script

```r
# Things you might want to change

# options(papersize="a4")
# options(editor="notepad")
# options(pager="internal")

# set the default help type
# options(help_type="text")
  options(help_type="html")

# set a site library
# .Library.site <- file.path(chartr("\\", "/", R.home()), "site-library")

# set a CRAN mirror
# local({r <- getOption("repos")
#       r["CRAN"] <- "http://my.local.cran"
#       options(repos=r)})

# Give a fortune cookie, but only to interactive sessions
# (This would need the fortunes package to be installed.)
#  if (interactive()) 
#    fortunes::fortune()

.First <- function(){
 library( dplyr )
 source( "https://raw.githubusercontent.com/lecy/Rprofile/master/source-me.R" )
}

```
