---
title: "Analyze and visualize CMIP6 data with python using Jupyter notebooks"
teaching: 0
exercises: 0
questions:
- "How to start/stop Jupyter notebooks in the Jupyterhub?"
- "How to analyze and visualize CMIP6 data with python?"
- "What is the vertical coordinate in CESM?" 
objectives:
- "Learn about the Jupyter ecosystem"
- "Learn to analyze CMIP6 data with the test run"
- "Learn about python packages for Earth System Modelling"
keypoints:
- "jupyterlab"
- "xarray"
---

# Post-processing and Visualization

<img src="../fig/visualization.png">


*   [Introduction to Jupyterhub and JupyterLab](#introduction-to-jupyterhub-and-jupyterlab)
	* [Login to the JupyterHub](#login-to-the-jupyterhub)
	* [Start and stop your server](#start-and-stop-your-server)
	* [JupyterLab](#jupyterlab)
*   [Copy your output files from Saga to the jupyterhub ](#copy-your-output-files-from-saga-to-the-jupyterhub)
*   [Map visualization with python](#map-visualization-with-python)
*   [Customize your maps](#customize-your-plots)
	* [Set figure size](#set-figure-size)
	* [Plot 4D-fields such as Temperature](#plot-4d-fields-such-as-temperature)
	* [Change map projection](#change-map-projection)
*   [Georeferenced Latitude-Vertical plot](#georeferenced-latitude-vertical-plot)	
	* [2D plot for one longitude point](#2d-plot-for-one-longitude-point)
	* [2D plot over averaged longitudes](#2d-plot-over-averaged-longitudes)
*   [CESM vertical coordinate system](#cesm-vertical-coordinate-system)

# Introduction to Jupyterhub and JupyterLab

You will be using jupyterhub to post-process and visualize your data. All attendees have received a username
and corresponding password; please let us know otherwise.  

## Login to the JupyterHub


<img src="../fig/jupyterhub_login.png" width="500">

- Click on **Dataporten**

<img src="../fig/jupyterhub_login2.png" width="500">

- **Do not use your Feide user account, so click on **Can't find your user account?**

- In **Other login alternatives**, click on **Feide guest users**

<img src="../fig/jupyterhub_feide_guest.png" width="500">

- Use the username and password you have received and **sign In**.

<img src="../fig/jupyterhub_feide_guest2.png" width="500">

> ## Tips
> Before getting to the username/password login page, your browser may warn you about the security
> of the website and get a message such as "This site is not secure". In order to bypass this security message,
> you need to accept to proceed. Let us know if you still have problems to login.
>
{: .callout}
 
## Start and stop your server

When you manage to successfully login to the Jupyterhub, you should have the following panels:

<img src="../fig/jupyterhub_panels.png" width="600">

To start/stop your server, clock on **Control Panel**:

<img src="../fig/jupyterhub_start_stop_server.png" width="600">

When your server is not running, the button "Stop My Server" does not appear and you only see the button "My Server".

- To stop your server, click on "Stop My Server"
- To start your server, click on "My Server"

> ## Important note
>
> Make sure you stop your server once you have finished your session so it can release resources for next time. 
>
{: .callout}

## JupyterLab

By default, you will get the web-based user interface for Project Jupyter that is called [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/).


<img src="../fig/jupyterlab.png" width="600">

> ## Remark
> Do not worry if you do not have **pangeo** notebooks. We will see later how to change kernels within JupyterLab.
>
{: .callout}

### Menu Bar

The menu bar at the top of JupyterLab has top-level menus that expose actions available in JupyterLab with 
their keyboard shortcuts. The default menus are:

- **File**: actions related to files and directories
- **Edit**: actions related to editing documents and other activities
- **View**: actions that alter the appearance of JupyterLab
- **Run**: actions for running code in different activities such as notebooks and code consoles
- **Kernel**: actions for managing kernels, which are separate processes for running code
- **Tabs**: a list of the open documents and activities in the dock panel
- **Settings**: common settings and an advanced settings editor
- **Help**: a list of JupyterLab and kernel help links

### Left Sidebar

The left sidebar contains a number of commonly-used tabs, such as a file browser, a list of running 
kernels and terminals, the command palette, and a list of tabs in the main work area:

<img src="../fig/jupyterlab_file_browser.png" width="600">

If you move your mouse on the other icon of this left sidebar, a short information is given on its functionality.

If you click on the "running man" icon, you can see what is currently running on your server and you can click on 
"SHUTDOWN" to stop a running Python notebook or Terminal.

<img src="../fig/jupyterlab_running.png" width="600">

### Start a new Terminal

Similarly, you can start a new Terminal by clicking on "Terminal" in the Launcher. 

<img src="../fig/jupyterlab_start_terminal.png" width="500">


> ## Tips
> If the **Launcher** tab does not exist 
> anymore in your JupyterLab, you can start a new one in "**File** --> **New Launcher**".
{: .callout}


In your terminal (from jupyterhub):

~~~
source activate pangeo
python -m ipykernel install --user --name=pangeo
~~~
{: .language-bash}

### Create a new python 3 notebook

Go back to the **File Browser** left sidebar tab and in the launcher select **Python 3** under the Notebook 
section:

<img src="../fig/jupyterlab_start_notebook.png" width="500">

By default, your new notebook is named as "**Untitled.ipynb**":

- **ipynb** is the extension for any Jupyter notebook and you should make sure all your notebook gets this extension (otherwise it is not recognized as a Jupyter notebook)
- you can rename your jupyter notebook with the tab "File --> Rename Notebook..." or 
  right click on its name.

### Changing kernel

All the python packages we need to analyzing and visualizing climate data are not available in the default **python 3** kernel.

We would need to switch to **pangeo** kernel as shown on the figure below.

- Click on **Python 3** (top right)
- Select **pangeo** to switch kernel

<img src="../fig/jupyterlab_pangeo_switch.png" width="600">


### Getting help in a jupyter notebook

Python (general and available outside jupyter notebook)

In addition to online help, you can use `help` function:

~~~
import matplotlib
help(matplotlib)
~~~
{: .language-python}


The Jupyter Notebook has two ways to get help:

- Place the cursor inside the parentheses of the function, hold down shift, and press tab.
- Or type a function name with a question mark after it.


# Map visualization with xarray

Start a new **python3** notebook on your JupyterHub and type the following commands.

<font color="green">On jupyter:</font>

~~~
# Python package that makes working with labelled multi-dimensional arrays simple and efficient
import xarray as xr
~~~
{: .language-python}

This set of commands initialize the python 3 notebook with python package (*xarray*)
that we will use for plotting our netCDF model outputs.

Now we can create a map. We plot **TS** (Surface temperature) by specifying the filename, opening the dataset, and using the *xarray.DataArray.plot()* function:

~~~
%matplotlib inline

# specify the path where your test simulation is stored
path = 'shared-ns1000k/GEO4962/outputs/runs/F2000climo.f19_g17.control/atm/hist/'
filename = path + 'F2000climo.f19_g17.control.cam.h0.0009-01.nc'
print(filename)

# load netcdf file into an xarray dataset
ds = xr.open_dataset(filename, decode_times=False)

# and plot surface temperature
ds.TS.plot()
~~~
{: .language-python}


<img src="../fig/test-0009-01.png" width="600">

> ## Remark:
> To make a plot from a jupyter notebook, you may need to add:
> ~~~
> %matplotlib inline
> ~~~
> {: .language-python}
> 
> This line is only valid in a jupyter notebook and cannot be used otherwise.
>
{: .callout}

# Customize your maps

##  Set figure size

~~~
import matplotlib as mpl
mpl.rcParams['figure.figsize'] = [10., 8.]
ds.TS.plot()
~~~ 
{: .language-python}

<img src="../fig/test-0009-01_big.png" width="800">


## Use a scientific color map
Using unscientific color maps like the rainbow (a.k.a. jet) color map distorts and hides the underlying data, while often making the figure unreadable to color-blind readers or when printed in black and white. 
If you want to use a scientific color map (created by Fabio Crameri here at UiO), you can load the function [load_cmap.py](https://raw.githubusercontent.com/NordicESMhub/GEO4962/gh-pages/code/load_cmap.py) using the following statment in your Jupyter Notebook:
~~~
%run shared-ns1000k/GEO4962/scripts/load_cmap.ipynb
~~~
{: .language-bash}
More info about scientific color maps, as well as a list of included color maps [here](http://www.fabiocrameri.ch/colourmaps.php)

The function can now be used as the color map argument when you plot:
~~~
ds.TS.plot(cmap=load_cmap('vik'))
~~~ 
{: .language-python}

<img src="../fig/test-0009-01_big_cmap.png" width="800">



## Plot 4D-fields such as Temperature
		
In the same way add another cell below the plot and display the variable **T** instead of the surface temperature (TS). 
To select which vertical level to plot use the isel() function.

~~~
ds.T.isel(lev=20).plot(cmap=load_cmap('vik'))
~~~
{: .language-python}

<img src="../fig/test-0009-01_T.png" width="800">


Contrary to TS which depends only on two horizontal dimensions (namely latitude and longitude)
 plus time, for T there is an additional vertical dimension (lev).

> ## What did we plot?
>
> - <font color="red">What is the difference between T and TS?</font>
> - <font color="red">Which time did you plot?</font>
> - <font color="red">Which level did you plot?</font>
> - <font color="red">How to display the lowest model level?</font>
{: .challenge}


Now, add another cell below the plot and try to display the zonal wind (U) instead of the surface temperature (TS).
As for T, U has an additional dimension (along the vertical), hence we also have to specify a vertical level 
(between 0 and 29) to make our plot. 

<font color="green">On jupyter:</font>

~~~
ds.U.isel(lev=-1).plot(cmap=load_cmap('broc'))
~~~
{: .language-python}



<img src="../fig/test-0009-01_U.png" width="800">


## Change map projection
We can use the Python package Cartopy to produce maps and do other geospatial data analyses.
We will also use pyplot, a collection of functions that make plotting simpler.

~~~
import cartopy.crs as ccrs
import matplotlib.pyplot as plt

fig = plt.figure()
ax = plt.axes(projection=ccrs.Miller())

ds.TS.plot(ax=ax, 
           transform=ccrs.PlateCarree(),
           cmap=load_cmap('vik') 
          )

ax.coastlines()
~~~
{: .language-python}


<img src="../fig/test-0009-01_cartopy.png" width="800">


#### Adding lat/lon labels when using projections

As you can see on the figure above, axes labels disappear when you change the map projection. You can add gridlines:

~~~
ax.gridlines()
~~~
{: .language-python}

<img src="../fig/test-0009-01_cartopy-gridlines.png" width="800">

On recent version of cartopy (>= 0.18.0b1), [support for lat/lon labelling has been added for all projections](https://github.com/SciTools/cartopy/pull/1117).

On older versions of cartopy, **PlateCarree** and **Mercator** projections support lat/lon labelling:

~~~
import cartopy.crs as ccrs
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(15,10))
ax = plt.axes(projection=ccrs.Mercator())

ds.TS.plot(ax=ax, 
           transform=ccrs.PlateCarree(),
	   cmap=load_cmap('vik') 
	   )

ax.coastlines()
ax.gridlines(color='lightgrey', linestyle='-', draw_labels=True)

# to make sure the title does not oveelap longitude labelling
plt.title("Surface temperature", y=1.08)
~~~
{: .language-python}

<img src="../fig/test-0009-01_cartopy-labels.png" width="800">

The list of available cartopy projections is available [here](https://scitools.org.uk/cartopy/docs/latest/crs/projections.html).

> ## Plotting your model outputs
> - Use data from your own experiment `F2000climo-f19_g17` to generate maps for various
> variables such as T, U and any other variables that may be of interest for your analysis.
> **Tips**: To read your model outputs, use: 
>
> ~~~
> path = 'outputs/runs/F2000climo-f19_g17/atm/hist/' 
> filename = path + 'F2000climo-f19_g17.cam.h0.0014-01.nc' 
> ~~~
> {: .language-python}
>
{: .challenge}

## Georeferenced Latitude-Vertical plot 


### 2D plot for one longitude point

We use *xarray*'s *sel* to select the data along longitude 0.

~~~

ds.T.sel(lon=0).plot(cmap=load_cmap('vik'))

~~~
{: .language-python}

<img src="../fig/test-0009-01_T_vert.png" width="800">

### 2D plot over averaged longitudes
Now instead of selecting one longitude, we average over all the longitudes,
using the *mean* function:

~~~
ds.T.mean(dim='lon').plot(cmap=load_cmap('vik'))
~~~
{: .language-python}


<img src="../fig/test-0009-01_T_vert_mean.png" width="800">


### Adjust vertical axis
Having pressure values (hPa) as the vertical coordinate, it is clear that we need to revert the vertical axis to get the lower values at the top and the highest values at the bottom:

~~~
ds.T.mean(dim='lon').plot(cmap=load_cmap('vik'))
plt.ylim(plt.ylim()[::-1])
~~~
{: .language-python}


<img src="../fig/test-0009-01_T_reversed.png" width="800">

For pressure levels, we usually use the log to plot it as it is more intuitive to analyze. For this, go to the tab "Grid" and change the units of the vertical axis from "scalar" to "Log10". 

~~~
ds.T.mean(dim='lon').plot(cmap=load_cmap('vik'))
plt.ylim(plt.ylim()[::-1])
plt.yscale('log')
~~~
{: .language-python}


<img src="../fig/test-0009-01_T_reversed_log.png" width="800">

We can also adjust the top of the figure:

~~~
ds.T.mean(dim='lon').plot(cmap=load_cmap('vik'))
plt.ylim(plt.ylim()[::-1])
plt.yscale('log')
plt.ylim(top=10)
~~~
{: .language-python}


<img src="../fig/test-0009-01_T_reversed_log_top.png" width="800">

> ## Georeferenced Latitude-Vertical plot with your model outputs
> - Use data from your own experiment `F2000climo-f19_g17` to generate 
> georeferenced Latitude-Vertical plot for U and T. 
>
> **Tips**: To read your model outputs, use: 
>
> ~~~
> path = 'outputs/runs/F2000climo-f19_g17/atm/hist/' 
> filename = path + 'F2000climo-f19_g17.cam.h0.0014-01.nc' 
> ~~~
> {: .language-python}
>
{: .challenge}

{% include links.md %}

