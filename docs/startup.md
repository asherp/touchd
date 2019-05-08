# Quickstart

The first order of business is to get a compatible python environment for TouchDesigner.
I prefer ```miniconda3``` for this. Miniconda avoids the pitfalls of a system-wide install
while giving you the flexibility to add whatever modules you'll need.

## Miniconda

To install ```miniconda3```, go [here](https://docs.conda.io/en/latest/miniconda.html).
Don't worry about the python version just yet, either one will do. (We'll specify the appropriate
python version when we create the environment below.)

After you download, run the installer and you should be able to run ```conda``` commands when you open a terminal.
To see what commands are available, run:

	conda --help

## Creating an environment

To create your TouchDesigner environment, run the conda command

	conda create -n touchd python==3.5 numpy==1.11.3

!!! note
    As of this writing, TouchDesigner uses python==3.5 and numpy==1.11.3. This will likely change in the future!


Now that your environment is created, you can activate it with

	conda activate touchd

This will change your command prompt to ```(touchd)$``` so you'll know you're working in it. From now on, any packages you install will be tied to this environment. 

## Pointing to the environment

Once you've got your environment set up, you need to inform TouchDesigner of the location of it's site packages - that is, the directory where all the installed libraries live. While your ```touchd``` environment is active, type:

	python -m site

Copy the path that ends in ```site-packages``` (under sys.path). Open TouchDesigner `->` edit `->` preferences `->` General `->` Python Module Path. Paste it there.

!!!note
    On Windows, you will likely have `\\` in the path. Replace those with `/`.

Close and reopen touch designer.

# Data Science packages

## Pandas

Pandas is perhaps the most ubiquitous data science package out there, being adept at remixing large arrays of data (so long as it fits in memory). The latest version of pandas prefers numpy >= 1.12.0, which is not what TouchDesigner currently uses. The earliest stable release of pandas that works with TouchDesigner is ```0.23.0```.

	pip install pandas==0.23.```0 so you'll know you're working in it. From now on, any packages you install will be tied to this environment. 

## Dask

If you find yourself needing handle datasets to large to fit in memory, then you should consider using [Dask](https://dask.org/). It allows you to easily launch tasks on multiple worker processes, has parallelized versions of pandas dataframes, several deployment options, and great documentation.