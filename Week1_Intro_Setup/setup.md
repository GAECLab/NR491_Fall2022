NR491 Fall 2022
Week 1 Lecture 2, Aug 26, 2022
 
# Software Installation

The purpose of this class period is to ensure you are set up for the course and you have the software working. We will use openly available and platform independent (Mac OS, Linux, Windows) software. Please install:
 
## **Python 3**:
using the anaconda distribution from [here](https://www.anaconda.com/distribution/).
 
A little blurb on which python version to download and how to download it using anaconda is available [here](http://www.acgeospatial.co.uk/python-geospatial-workflows-prt1-anaconda/)
 
## **Anaconda environments**: 
Conda is a very useful package and environment manager that allows you to use commands at the Anaconda Prompt for Windows, or in a terminal window for macOS or Linux.

Once you have anaconda installed you can try the following commands.

To check which conda version you have at the terminal on Mac or the Anaconda Prompt on Windows type:

`conda --version`
 
To update conda:

`conda update conda`

**Managing conda environments** we can use different environments containing different files, packages and their dependencies. It is a good practice to not use your base environment when working on multiple projects. You can create different environments and keep your projects independent from each other. All you need to do is create and activate your environment for your respective project. Read about environments here. 

One way to create a conda environment is to use an existing file such as a *yml file* that has information on the libraries you’d like to add - use the yml file in your folder to create your NR491 environment. To do so type the following at the terminal on Mac or the Anaconda Prompt on Windows:
 
`conda env create -f NR491.yml`
 
To activate your conda environment:

`conda activate NR491`

To list all of your environments:

`conda info --envs`
 
To deactivate an environment:
 
`conda deactivate NR491`
 
To remove an environment:

`conda env remove --name NR491`
 
Check this on-line documentation on how to use anaconda. This cheat sheet is also helpful.

## **VS Code**: 
is a very powerful code editor that allows you to work with multiple coding languages (e.g., Python, R, HTML, javascript, etc.) all in one code environment. It is very convenient when working on several projects simultaneously. You can download it from [here](https://code.visualstudio.com/).

**Installing the Python extensions in VS Code**: after installing VS Code you will need a couple of extensions to work with Python scripts, Jupyter Notebooks, etc. Below are common extensions that you will need to install:
Microsoft Python Extension for Visual Studio Code
Anaconda Extension Pack 
Code Runner
 
## **QGIS v3.1X.X**: 
to download the most updated version, please follow the instructions at this [link](https://www.qgis.org/en/site/forusers/download.html).
 
## **Git**:
is a version control system to handle programming projects that allows code sharing through an online platform (e.g., Github, Bitbucket, etc.). Download it from [here](https://git-scm.com/downloads)


# **On-line Tutorials**:
If you are not familiar with the software mentioned above please use on-line tutorials to familiarize yourself with them. Some suggestions are included below.
 
**Python tutorials**: **DataCamp** has several free online tutorials including [Python Data Structures Tutorial](https://www.datacamp.com/tutorial/data-structures-python) and [Free Data Camp Intro to Python](https://www.datacamp.com/courses/intro-to-python-for-data-science).


**LinkedIn Learning**: examples of free tutorials include [Python Essential Training](https://www.linkedin.com/learning/python-essential-training-14898805) and [Python for Data Science](https://www.linkedin.com/learning/python-for-data-science-essential-training-part-1/what-you-should-know?trk=teams_share). You will need to authenticate your NCSU email account to get free access to these tutorials! Check how to set up your account here at this [link](https://www.lib.ncsu.edu/faq/how-do-i-access-linkedin-learning-nc-state-community-member).


**A Whirlwind Tour of Python** book is a good and free resource, available [here](https://jakevdp.github.io/WhirlwindTourOfPython/).


**Python in VS Code**: a very good intro of how python and VS Code work together is [here](https://code.visualstudio.com/docs/languages/python) and [here](https://code.visualstudio.com/docs/python/python-tutorial).


**Jupyter Notebooks**: to learn how to use jupyter notebooks in VS Code you can use the tutorial available [here](https://code.visualstudio.com/docs/python/jupyter-support).


As we progress through the semester you may find the **Python for Data Science Handbook** available [here](https://jakevdp.github.io/PythonDataScienceHandbook/) a useful resource.
 

**QGIS**: LinkedIn Learning has a nice QGIS online course Learning QGIS [here](https://www.linkedin.com/learning/learning-qgis-2/exploring-the-powerful-world-of-qgis?trk=teams_share).


**Q-GIS Semi-Automatic Classification Plugin (SCP)** is a very useful tool to perform supervised classification, download, pre- and post-processing satellite imagery. SCP has several online tutorials, which you can find [here](https://fromgistors.blogspot.com/search/label/Tutorial?max-results=10). Their documentation [here](https://readthedocs.org/projects/semiautomaticclassificationmanual/downloads/pdf/latest/) is pretty good.

**Git**: a couple of useful links are [here](https://git-scm.com/doc), [here](https://git-scm.com/video/what-is-git), [here](https://git-scm.com/book/en/v2), and [here](https://ndpsoftware.com/git-cheatsheet.html#loc=stash).


