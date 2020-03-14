---
title: STATS 531 Winter 2020  pomp installation instructions
---

<style type="text/css">
div .nb {
	background-color: #ffeca3;
	border-style: solid;
	border-width: 2;
	border-color: #00274c;
	padding: 1em;
}
hr {
	border-width: 3;
	border-color: #00274c;
}
</style>

------------------------------

Please read the appropriate sections below, which give specific instructions for installing and testing the software we will be using.

<div class="nb"> 

**Important note:** If you run into problems, send a note to ionides@umich.edu with a detailed description of the problem you've encountered.
In this message, **be certain to include all of the following information**:

- the operating system you’re running,
- the version numbers of **R**, **Rstudio**, and **pomp** you’re attempting to install,
- what command(s) you've executed, and
- what error messages you've received.

In particular, it is often easiest to send a screenshot or transcript showing the commands you've entered and the error messages you've received.
In **R**, you can run `Sys.info()` to get a printout of the operating system and software version numbers.

</div>


### Update **R** and **RStudio**

The latest version is **R** 3.6.3, and it is helpful to use a current version, say 3.6.1 or later.
If you need to update, go ahead and install version 3.6.3.
Source code and binaries are available on CRAN (https://cran.r-project.org/).
Install *the latest version* of **RStudio** from [rstudio.com](https://www.rstudio.com/products/rstudio/download/).

### Install needed packages

Open a session in **RStudio** and run the following:

```
> update.packages()
> source("https://ionides.github.io/531w20/pomp_prep/packages.R")
```

*[The `>` is the command prompt; it is not part of the command.
Also, depending on your email client program, you may need to replace the quotation marks with plain keyboard double quotes.]*

The first command updates your installed packages.
You may be prompted to specify a CRAN mirror:
choose one geographically near you.
In **RStudio**, you can also push the "Update" button on the "Packages" tab to accomplish this.

The second command runs a script which will install some packages needed to run code from the notes. It is probably helpful to install these.

-------------------------------

## Windows users

If your machine runs Windows, you must install **Rtools**.
This will give you the ability to compile C code and dynamically link it into an **R** session.

[Download **Rtools** from CRAN](https://cran.r-project.org/bin/windows/Rtools/) and install it.
When installing **Rtools**, it is sufficient to choose the “Package authoring installation” option.
Also during the installation, **you must tick the "edit system PATH" box**.

If, having installed the latest version of **Rtools** compatible with your **R**,  the scripts below fail, try installing a "frozen" version of **Rtools**.

***It is critical that you install these programs before the course starts!***

-------------------------------

## MacOSX users

So that you can compile C code and dynamically link it into an **R** session, you will need to have the **Xcode** app installed.
This is gratis and can be installed via the App Store or downloaded from [developer.apple.com](https://developer.apple.com/download/).

Note that you must go beyond merely installing the **Xcode** app.
After you've installed the app, open a unix terminal (listed as the **Terminal** app under "Utilities" in the Finder) and run the following line
```
xcode-select --install
```
This will install the "Command Line Tools" that are needed to compile native C codes.

------------------------------------

## All users

### Test **pomp**

Open a session in **RStudio** and run the following:
```
> source("https://ionides.github.io/531w20/pomp_prep/pompTest.R")
```
This will check whether you can work with **pomp**.

If it fails, try the following:
```
> source("https://ionides.github.io/531w10/pomp_prep/hello.R",echo=TRUE)
```
If this fails to give the "Hello!" message, you will need to follow the instructions below that correspond to your OS before re-trying the `pompTest.R` script.

### Linux and unix

If you have trouble with any of the scripts above, make sure you have the GNU compiler collection (GCC), including **gfortran**, installed on your computer.
Linux distributions typically include this by default but it is not impossible that you have somehow avoided this.

### MacOSX

If the `pompTest.R` script fails because you cannot load **pomp**, try installing it from source.
The easiest way to do this is to use the **devtools** package.
Do
```
install.packages("devtools")
library(devtools)
install_github("kingaa/pomp")
```
If, while trying to install from source, you receive the error,
```
make: gfortran-4.8: No such file or directory
```
or one that otherwise refers to `gfortran`, then it is likely that you do not have the necessary version of **gfortran** installed.
Have a look at [these instructions](https://kingaa.github.io/mac-fortran.html) and email me if these don’t work for you.

Some users have reported receiving an error complaining that 
```
'stdlib.h' file not found
```
This indicates that the command-line tools from **Xcode** have not been properly installed.
In a unix terminal, run 
```
xcode-select --install
```
to correct this problem.

### Windows

You have probably failed to install the **Rtools** correctly.
Revisit the [instructions above](#windows-users).

---------------------------

## Acknowledgments

This material leans heavily on Aaron King's instructions for [setting up an R environment for pomp](https://kingaa.github.io/sbied/prep/preparation.html). 

------------------------------
