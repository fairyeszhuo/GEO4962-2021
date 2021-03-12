---
title: "Analyze and visualize CMIP6 data with python using Jupyter notebooks"
teaching: 0
exercises: 0
questions:
- "How to analyze and visualize CMIP6 data with python?" 
objectives:
- "Learn about the Jupyter ecosystem"
- "Learn to analyze CMIP6 data on model topics"
- "Learn about python packages for Earth System Modelling"
keypoints:
- "jupyterlab"
- "xarray"
---

<!-- # Post-processing and Visualization -->
# Visualization

<img src="../fig/visualization.png">

*   [Map visualization with python](#map-visualization-with-python)
*   [Customize your maps](#customize-your-plots)
	* [Set figure size](#set-figure-size)
	* [Plot 4D-fields such as Temperature](#plot-4d-fields-such-as-temperature)
	* [Change map projection](#change-map-projection)
*   [Georeferenced Latitude-Vertical plot](#georeferenced-latitude-vertical-plot)	
	* [2D plot for one longitude point](#2d-plot-for-one-longitude-point)
	* [2D plot over averaged longitudes](#2d-plot-over-averaged-longitudes)
*   [Adjust vertical axis](#Adjust-vertical-axis)


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

