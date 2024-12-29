---
title: "How to install the specific version of Python with Anaconda?"
source: "https://stackoverflow.com/questions/57940783/how-to-install-the-specific-version-of-python-with-anaconda"
author:
  - "[[Stack Overflow]]"
published: 2019-09-15
created: 2024-11-23
description: "I want to install Anaconda with Python Version 3.6.5. If I install Anaconda3-5.2.0, It install Python 3.5.1.  Where to download the Anaconda with Python 3.6.5.  The Big Data Scripts work only with"
tags:
  - "clippings"
---
I want to install Anaconda with Python Version 3.6.5. If I install Anaconda3-5.2.0, It install Python 3.5.1. Where to download the Anaconda with Python 3.6.5. The Big Data Scripts work only with Anaconda Python 3.6.5.

[

![DennisLi's user avatar](https://lh4.googleusercontent.com/-xbiq_0X1UQc/AAAAAAAAAAI/AAAAAAAAABQ/XyC6SkmIKn4/photo.jpg?sz=64)

](https://stackoverflow.com/users/6169688/dennisli)

[DennisLi](https://stackoverflow.com/users/6169688/dennisli)

4,1286 gold badges35 silver badges71 bronze badges

asked Sep 15, 2019 at 2:49

[

![user12068803's user avatar](https://www.gravatar.com/avatar/bcab57e86349f74db882aea9b814f562?s=64&d=identicon&r=PG&f=y&so-version=2)

](https://stackoverflow.com/users/12068803/user12068803)

2

## Anaconda Downloads

The Anaconda distribution with Python 3.6.5 was **version 5.2.0**.<sup><strong>1</strong></sup> You can download this from [the Anaconda distribution archive](https://repo.continuum.io/archive/). If you do install from this, then make sure to update Conda immediately after installation:

```python
conda update conda
```

However, **I strongly recommend the following alternate solution** as better practice.

## Miniconda + Anaconda environment

### Reasoning

What is installed in the **base** environment is relatively fixed once installed. Ultimately, you don't want to mess with your **base** environment, so best practice is to have the latest version there. Fortunately, you don't have to install a full Anaconda distribution, but rather can use a lightweight Miniconda (or Miniforge) distribution and create a secondary environment for the purpose of having an Anaconda Python 3.6.5 distribution. In the long run this will give you better stability.

### Steps

1. Download and install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or a [Miniforge variant](https://github.com/conda-forge/miniforge#miniforge). Once that is working...
2. Create your Anaconda env:

```python
 conda create --name my_env -c anaconda python=3.6.5 anaconda=5.2.0
```
3. Use your new isolated env:

```python
 conda activate my_env
```

---

<sub><strong>[1]</strong> I determined this by running <code>conda create -n foo --dry-run -c anaconda python=3.6.5 anaconda</code> and then examining the version of the <code>anaconda</code> package that Conda ended up with in the solve.</sub>

answered Sep 15, 2019 at 3:47

[

![merv's user avatar](https://i.sstatic.net/t831Y.jpg?s=64)

](https://stackoverflow.com/users/570918/merv)

[merv](https://stackoverflow.com/users/570918/merv)merv

75.9k17 gold badges208 silver badges273 bronze badges

Also try

```python
conda install python=3.6.5
```

but you may encounter some incompatibility issues with other packages.

Alternatively, you may want to try creating a new environment. From the anaconda prompt, create a custom environment and specify the repository channel to find the version

```python
conda create --name py365 python=3.6.5 --channel conda-forge
```

Activate the new environment

```python
conda activate py365
```

However, the activation will not be permanent, and you will need to activate each time you start the anaconda prompt.

answered Sep 15, 2019 at 3:14

[

![Stoner's user avatar](https://www.gravatar.com/avatar/aa7e13445ee80101795f63cedbd67194?s=64&d=identicon&r=PG&f=y&so-version=2)

](https://stackoverflow.com/users/7777183/stoner)

[Stoner](https://stackoverflow.com/users/7777183/stoner)Stoner

9061 gold badge10 silver badges33 bronze badges

In your anaconda prompt, you can manually update your python to the latest version with :

```python
conda update python
```

In case you are not familiar with it, anaconda prompt is installed to your computer when you install anaconda. Just make a search for it on your computer.

You can refer to this post : [How do I upgrade to Python 3.6 with conda?](https://stackoverflow.com/questions/41535881/how-do-i-upgrade-to-python-3-6-with-conda)

answered Sep 15, 2019 at 3:05

[

![Gonzalez87's user avatar](https://lh4.googleusercontent.com/-9UhE0S-ugcI/AAAAAAAAAAI/AAAAAAAAAJ0/qWllnoiULx4/photo.jpg?sz=64)

](https://stackoverflow.com/users/11563220/gonzalez87)

[Gonzalez87](https://stackoverflow.com/users/11563220/gonzalez87)Gonzalez87

1721 silver badge10 bronze badges
