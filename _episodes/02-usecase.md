---
title: Getting started
teaching: 20
exercises: 20
questions:
  - What is the dataset that we are working with?
  - How do I write my first Python code in a Notebook?
  - Why do we need to use an environment manager such as conda?
objectives:
  - Introduce the dataset used throughout the course.
  - Understand why the need for environments in Python.
  - Start up your Jupyter notebook and write your first line of code in Python.
keypoints:
  - Environments are required to separate projects with different software requirements.
  - Installation of new software can be done using package managers such as `pip` and `conda`.
---

# Background

In an increasingly data‑driven world, governments have made more and more datasets available for public consumption. Singapore is no exception. In an effort to promote transparency, over 5,000 datasets from 65 different agencies have been made freely available at [DataGovSG](data.gov.sg).

These datasets cover a wide range of topics — from demographics and transport, to weather, health, and economic indicators. To make them easily accessible, many are served through APIs, allowing developers, researchers, and businesses to query the data programmatically rather than downloading static files.

For example, instead of downloading a CSV of daily weather records, an application can send an HTTP GET request to the data.gov.sg API and immediately receive the latest data in JSON format. This makes it possible to build real‑time dashboards, mobile apps, or data‑driven services that are always up to date.

In the codes provided in the notebooks, we will be using `python` to extract 24-hour weather forecasts made available by NEA. The API URL that we will be using is the following: [https://api-open.data.gov.sg/v2/real-time/api/twenty-four-hr-forecast?date=2025-01-01](https://api-open.data.gov.sg/v2/real-time/api/twenty-four-hr-forecast?date=2025-01-01).

# Setting up your VSCode for working with Jupyter notebooks

{: .checklist}

> ## Prerequisite
>
> It is assumed that you have already installed Python, VSCode and conda. If you had any difficulties, please raise your hands and a facilitator will be with you shortly to help you with the installation.

There are various avenues by which we can write and run codes in Python. Python codes can be executed interactively (write and execute) or as a script. Through the course of the workshop, we will be using Jupyter notebooks to write and run our Python codes. All this will be run in VSCode. The main steps we will do here are the following:

1. Create an **environment** using conda.
2. Install the **jupyter** package in our new environment.
3. Create a **jupyter notebook** for interactively writing Python codes.

# Environments as isolated compartments within the operating system

As the number of projects you do increase, so will the number of conflicting software dependencies. It is hence crucial that we are able to created isolated environments for each project. All the software required for a project, including specific versions, need to be contained within this isolated environment. How can we create these environments? For those who are really rich, you can simply purchase one new computer for each project you undertake. But that will clearly not be a sensible option. Another approach is to create virtual environments. This is where environment managers come in. `conda` is a widely used environment manager. With `conda`, we are able to do the following:

1. Create isolated environments so projects don’t conflict with each other.
2. Manage packages and dependencies with a single command.
3. Reproduce environments easily across different machines or collaborators.

Assuming you had downloaded and installed `conda`, you will create your first environment, `introductory_python`, in the command line (Terminal for Mac OSX users, Powershell for Windows users), as follows:

{:.code}

```
conda create -n introductory_python python=3.12
```

This will create a new `conda` environment called `introductory_python`. Importantly, we had also told `conda` to download and install the python version 3.12 (`python=3.12`). The ability to specify exact versions is important for reproducibilty -- as software packages are updated, some of the internals might change and become incompatible with other software packages we are using. In some cases, functions are deprecated or their behaviours changed. For that reason, it always pays to be mindful of which software versions we are using in our work. We can create a file called `requirements.txt` which captures all the software packages and version numbers in our environment so that someone else can reproduce our work entirely.

Once you have created a new environment, we will activate the environment by doing the following:

{:.code}

```
conda activate introductory_python
```

We can deactivate the environment by doing `conda deactivate`. To get a list of all the environments installed, we can do `conda env list`.

{:.challenge}

> ## Creating a new enviroment
>
> In this simple exercise, create a new python environment called `python3_11` which will use python 3.11 instead. Verify that your new environment uses the correct version of Python by calling `python` from the environment.
> {:.solution}
>
> > ## Solution
> >
> > ```
> > conda  create -n python_311 python=3.11
> > ```

{: .discussion}

> ## Environment for this workshop
>
> For this workshop, which environment you use doesn't matter. Go ahead and delete one of them using `conda env remove -n <name>`

# Installation of software package: A formidible task

Installation of software might seem like a straight-forward task. Just download a binary (`.exe`, `.dmg`), click and run, and you are done. Unfortunately, this is not the case with the installation of Python libraries (and other programming languages, really).

Imagine you want to use a library called `coolscience`, but it requires:

- `numpy` version 1.19 or older
- `matplotlib` version 3.3

while another library you need demands the latest numpy and a different version of matplotlib.

Suddenly, you’re stuck: whichever version you install, something breaks. This is known as **dependency hell** — the frustrating situation where software libraries (dependencies) require conflicting versions of each other. This is a relatively common experience for many system administrators. Getting yourself out of this isn't trivial - it is the stuff of nightmares, and sometimes, it is easier to simply give up, delete everything you have installed, find a bar to get a drink to drown your sorrows, and wonder why did you even get started.

Another scenario that makes installation difficult looks like this. Imagine you want to use library called `terriblepackage`, which requires:

- `package1` version 2 or newer.
- `package2` version 1

In turn, `package1` and `package2` each requires another 10 dependencies. Suddenly, in order to install `terriblepackage`, we will need to install 20 software packages. Oh, and what if each of the dependencies require 2 more dependencies each? We now have an endless rabbit hole of finding packages and making sure the version numbers match. Throw in version incompatibility,
and suddenly, you start thinking `terriblepackage` was indeed a well-named package.

Thankfully, these situations are rare nowadays with the introduction of package managers. The most common package manager for Python is `pip`, which comes installed with Python by default. `conda` can also be used to install packages (as described above). Here, we will install `jupyter`, an interactive environment for us to write and execute python codes, in our newly created environment.

{:.callout}

> ## Caution
>
> Make sure that you have activated the workshop environment by using `conda activate introductory_python`. You generally want to avoid installing in the base environment.

{:.code}

```
conda install -c conda-forge jupyter
```

You will be asked if you will like to install a long list of dependencies. Type `y` and wait for conda to do it's magic.

{:.callout}

> ## Channels
>
> You will notice that we can added `-c` in our `conda install` command. This tells `conda` to search for the package from the `conda-forge` channel. You can think of channels as repositories. By passing the `-c`, we are telling `conda` to download the package from the `conda-forge` channel. `conda-forge` is a common channel; another that I have used extensively is `bioconda`.

{:.challenge}

> ## Try it yourself
>
> Try to install the package `black`, which is available from the `conda-forge` channel.

# Conclusion

At this point, you should have a working python environment with jupyter installed. We will now fire up VSCode and open the `day1.ipynb`. At this point, VSCode should prompt you to install the `jupyter` extension from the marketplace. Go ahead and install this extension. (It will make your life significantly easier, trust me).
