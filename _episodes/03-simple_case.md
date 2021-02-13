---
title: "Get familiar with netCDF data format and the visualization process"
teaching: 30
exercises: 60
questions:
- "What is netCDF data format?"
- "How to quickly inspect and visualize netCDF data files?"
objectives:
- "Learn about netCDF data format"
- "Learn to inspect a netCDF file"
- "Learn to quickly visualize a netCDF file"
keypoints:
- "data visualization"
- "High-Performance Computing"
- "netCDF"
- "ncdump"
- "ncview"
---


# First practical: open a netCDF data file

<img src="../fig/practicals.jpg">

We do all the practicals at <font color="red">Jupyterhub</font>.  

*   [First look at a CMIP6 data file](#First-look-at-a-CMIP6-data-file)
	*   [What is a netCDF file](#What-is-a-netcdf-file)
	*   [Inspect a netCDF file](#inspect-a-netcdf-file)
	*   [Quick visualization of a netCDF file](#quick-visualization-of-a-netcdf-file)

### First look at a CMIP6 data file
#### What is a netCDF file?

Netcdf stands for “network Common Data Form”. It is self-describing, portable, metadata friendly, supported by many languages
(including python, R, fortran, C/C++, Matlab, NCL, etc.), viewing tools (like panoply, ncview/ncdump) and tool suites of file operators (in particular NCO and CDO).

#### Inspect a netCDF file

NetCDF files are often too big to open directly (with your favorite text editor, for instance), however one can look at the **content** of a netCDF file instead, for example to *dump* the **header** of one of the netCDF history files.

<font color="red">Open a terminal at Jupyterhub:</font>

~~~
module load netCDF/4.6.1-intel-2018b
cd /cluster/work/users/$USER/archive/F2000climo-f19_g17/atm/hist/
ncdump -h F2000climo-f19_g17.cam.h0.2000-06.nc
~~~
{: .language-bash}

~~~
netcdf F2000climo-f19_g17.cam.h0.2000-06 {
dimensions:
        lat = 96 ;
	lon = 144 ;
	time = UNLIMITED ; // (1 currently)
        nbnd = 2 ;
        chars = 8 ;
        lev = 32 ;
        ilev = 33 ;
variables:
        double lat(lat) ;
                lat:_FillValue = -900. ;
                lat:long_name = "latitude" ;
                lat:units = "degrees_north" ;
        double lon(lon) ;
                lon:_FillValue = -900. ;
                lon:long_name = "longitude" ;
                lon:units = "degrees_east" ;
        double gw(lat) ;
                gw:_FillValue = -900. ;
                gw:long_name = "latitude weights" ;
    ....
~~~
{: .output}

{% include links.md %}

