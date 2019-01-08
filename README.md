# Experimetrics BITSS Workshop
Resources for the workshop on dynamic documents at Universidad del Rosario

---

Please check back often for new and updated materials

---
## Table of Contents

- [Setting up Git and Github Desktop](#Setting-up-Git-and-Github-Desktop)
- [Setting up Notepad++](#Setting-up-Notepad\+\+)
- [Setting up Jupyter Notebooks and RStudio](#Setting-up-Jupyter-Notebooks-and-RStudio)
  - [Installing the Stata kernel for Jupyter Notebooks](#Installing-the-Stata-kernel-for-Jupyter-Notebooks)
- [Troubleshooting](#Troubleshooting)

---
If you have issues installing/configuring, please open up an issue on this GitHub page

If you have any complaints, please email:

Oscar Barriga Cabanillas
obarriga@ucdavis.edu

If you have any praise, please email:

Aleksandr Michuda
amichuda@ucdavis.edu


---

## Setting up Git and Github Desktop

In order to do this, please go to [https://desktop.github.com/](https://desktop.github.com/) and download the Github Desktop Application.

- For MacOs/Windows Users, you can download directly from the website and install.
- For Linux users, there is no desktop application available, but the ```git``` commandline utility is probably already installed on your system.

Afterwards, please make an account on Github. You will be asked to put in this information when you launch the Github Desktop application.

As a proof-of-concept/exercise, once you have everything set up, go to ```clone a repository```, the URL tab and put in [https://github.com/lordflaron/Experimetrics-BITSS-Workshop.git](https://github.com/lordflaron/Experimetrics-BITSS-Workshop.git), the git clone URL for our repository. Afterwards, there will be a folder with all the workshop materials. You have "cloned" the repository on Github. Congratulations! 

## Setting up Notepad++ 

Please install Notepad++ from [https://notepad-plus-plus.org/download/v7.6.html](https://notepad-plus-plus.org/download/v7.6.html)

For Windows Users: There is an installer available.
For MacOs/Linux: There is sadly no installer available for this application, but you can still use the do-file editor for the Stata portion of the workshop.

Please follow these instructions to integrate Stata with Notepad++
[https://donlelek.github.io/2015-01-16-integrate-TE-with-stata/](https://donlelek.github.io/2015-01-16-integrate-TE-with-stata/)


## Setting up Jupyter Notebooks and RStudio

To install Jupyter Notebooks and Rstudio, please go to [https://www.anaconda.com/download/](https://www.anaconda.com/download/) and download the Python 3.7 version of the Anaconda Distribution. This application installs a Python and R environment on your desktop, as well as some helpful libraries and applications for scientific computing. **Even if you do not plan on using Python or R in the future, (which would be a shame, but regardless) please install this application.** 


After a lengthy installation process, you will have access to Rstudio and Jupyter notebook from the Anaconda Navigator (and notice that there is also a program called Anaconda Prompt, this will be important later). Although Jupyter Notebooks should be installed, RStudio may not be. Please go to Anaconda Navigator (it may take a while to load) and in the RStudio box, click install. If Jupyter notebooks does not show as installed, please click to install it as well.

### Installing the Stata kernel for Jupyter Notebooks

Jupyter Notebooks come with so-called "kernels." The kernels are basically the language that will interpret your code. But the beauty of Jupyter notebooks is that they don't need to only have a Python kernel. In fact, for our purposes, a clever guy developed a Stata kernel, that will make our life very easy. The website for the kernel is [here](https://kylebarron.github.io/stata_kernel/). 

We are going to go through the installation process, but his website has instructions on how to install the stata kernel, as well as some more advanced techniques that would be useful for scientific computing (some of which we will talk about).

#### Checking if ```pip``` is installed

In order to install the Stata kernel, we need to use ```pip```, a Python program that hosts Python programs (that's so meta). To do this, go to *Anaconda Prompt* (which I mentioned before) and type:

``` 
pip --help
```

If you get output from the ```pip``` command, you're GREAT!

If this is your first foray into using a commandline, congratulations, you are now a Hacker(wo)man.
![alt text](http://peroty.com/blog/wp-content/uploads/2015/06/HACKERMAN.png "You did it!")

#### Installing the Stata Kernel

**Note for Windows Users**: Please follow the steps in [https://www.stata.com/automation/#install] to register your Stata with your computer before installing. 

After this, in the same Anaconda Prompt, you have open now, type:

```
pip install stata_kernel
python -m stata_kernel.install
```

If you get an error about needing to set your Stata path manually, please refer to [Troubleshooting](#Troubleshooting), on the question about your kernel always dying. After this you should be done! To check if the installation worked, go to Anaconda Navigator and open a Jupyter Notebook. In the top right corner, there will be a button for ```New``` and in the dropdown menu, you should see Stata as an option.

If you have any concerns or problems, please email us.

## Troubleshooting

1. > My kernel starts, but it keeps dying! What do I do?

This may be due to the stata path not being defined. There will be a file called ```.stata_kernel.conf``` in your home directory:

For Windows Users: C:/Users/\<your username\>

For Linux: /home/\<your username\>

For Mac: /Users/\<your username\>

Inside the ```.stata_kernel.conf```, you will find a variable called ```stata_path```. Write, as a string, the location of the Stata executable you are using. An example would be:

```
stata_path = "C:\Users\<your username>\Stata 15\Stata15-se.exe"
```

It should now be working!

2. > My kernel doesn't start and the the console states `
AttributeError: 'StataSession' object has no attribute 'stata'`

That is recent bug that has been squashed (see issue [here](https://github.com/kylebarron/stata_kernel/issues/281). Try upgrading the stata kernel: `

```
pip install stata_kernel --upgrade
```

Then run:

```
pip show stata_kernel
```

The version should say 1.10.1.


  
