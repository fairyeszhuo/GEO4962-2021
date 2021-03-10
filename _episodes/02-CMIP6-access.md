---
title: "Get familiar with CMIP6 data and the netCDF data visualization process"
teaching: 30
exercises: 60
questions:
- "How to get access to Jupyterhub?"
- "How is the CMIP6 data stored?"
- "What is netCDF data format?"
- "How to quickly inspect and visualize netCDF data files?"
objectives:
- "Learn about CMIP6 data"
- "Learn about netCDF data format"
- "Learn to inspect a netCDF file"
- "Learn to quickly visualize a netCDF file"
keypoints:
- "Jupyterhub"
- "CMIP6 data visualization"
- "netCDF"
- "ncdump"
- "ncview"
---

#  Setup instructions for accessing Jupyterhub

The CMIP6 data analysis will be conducted directly at [jupyterhub](https://jupyter.org/hub). We will be using [https://climate.uiogeo-apps.sigma2.no/](https://climate.uiogeo-apps.sigma2.no/).

- You should have received an email message titled "JupyterHub links for GEO4962". If not please request it to the course organizers.
- Follow "invitation link" in the email message
- If you don't already have a Feide guest user account (otherwise skip this step), click "Feide guest users".
    - register a new account (do not use your UiO username as it may be confusing for everyone).
    - finish the registration process
    - click again on the "invitation link" in the email
- Login with "Feide guest users"
- Accept the different policies
- Agree to become a member of the **NS1004K**: the browser should display the message "Loading group details"
- Now go to [GEO4962 Jupyterhub](https://climate.uiogeo-apps.sigma2.no/)
- Click "Sign in with Dataporten"
- Login with Feide Guest User (Not your UiO username)
- Finally the web browser should display a page with "jupyterlab" on the upper left side


For later usage of the notebooks just use the [GEO4962 Jupyterhub link](https://climate.uiogeo-apps.sigma2.no/)

 
The main advantage of using this machine is that your data are directly accessible from anywhere through a web 
interface and the necessary post-processing and visualization packages we need are already available. 

# CMIP6 data in [GEO4962 Jupyterhub](https://climate.uiogeo-apps.sigma2.no/)

Structure: 

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

