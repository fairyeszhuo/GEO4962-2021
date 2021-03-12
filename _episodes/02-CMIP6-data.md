---
title: "CMIP6 data and netCDF data format"
teaching: 0
exercises: 0
questions:
- "How is the CMIP6 data stored?"
- "What is the netCDF data format?"
- "How to quickly inspect and visualize netCDF data files?"
objectives:
- "Learn about CMIP6 data"
- "Learn about netCDF data format"
- "Learn to inspect a netCDF file"
keypoints:
- "CMIP6 data"
- "netCDF"
- "ncdump"
---

*   [CMIP6 data in GEO4962 Jupyterhub](#CMIP6-data-in-GEO4962-Jupyterhub)
  *   [Overview of CMIP6 data Structure](#Overview-of-CMIP6-data-Structure)
  *   [Find CMIP6 model data](#Find-CMIP6-model-data)
  *   [First look at a CMIP6 data file](#First-look-at-a-CMIP6-data-file)

# CMIP6 data in [GEO4962 Jupyterhub](https://geo4962.tacco.sigma2.no/)

The CMIP6 model data can be found in the **shared-tacco-ns1004k-cmip** folder. 

The NorESM model data is in a separate directory and can be found in the **shared-tacco-ns1004k-cmroot** folder.

## Overview of CMIP6 data Structure 

CMIP6 model data in **shared-tacco-ns1004k-cmip**

structure: shared-tacco-ns1004k-cmip/model-institute/model-name/experiment/ensemble-member/data-frequency/variable/grid/data-version

NorESM model data in **shared-tacco-ns1004k-cmroot**

structure: shared-tacco-ns1004k-cmroot/model-name/experiment/data-version/

Data filename format: variable_data-frequency_model-name_experiment_ensemble-member_grid_time-period.nc

## Find CMIP6 model data

- To find historical monthly zonal wind data of **CESM2/WACCM** model
~~~
cd ~/shared-tacco-ns1004k-cmip/NCAR/CESM2-WACCM/historical/r1i1p1f1/Amon/ua/gn/v20190227/
ls
~~~
{: .language-bash}

~~~
ua_Amon_CESM2-WACCM_historical_r1i1p1f1_gn_185001-201412.nc
~~~
{: .output}

- To find historcal daily precipitation data of **MPI-ESM** model
~~~
cd ~/shared-tacco-ns1004k-cmip/MPI-M/MPI-ESM1-2-HR/historical/r1i1p1f1/day/pr/gn/v20190710
ls
~~~
{: .language-bash}

~~~
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18500101-18541231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18550101-18591231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18600101-18641231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18650101-18691231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18700101-18741231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18750101-18791231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18800101-18841231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18850101-18891231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18900101-18941231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_18950101-18991231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19000101-19041231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19050101-19091231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19100101-19141231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19150101-19191231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19200101-19241231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19250101-19291231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19300101-19341231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19350101-19391231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19400101-19441231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19450101-19491231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19500101-19541231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19550101-19591231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19600101-19641231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19650101-19691231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19700101-19741231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19750101-19791231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19800101-19841231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19850101-19891231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19900101-19941231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_19950101-19991231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_20000101-20041231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_20050101-20091231.nc
pr_day_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_20100101-20141231.nc
~~~
{: .output}


- To find historcal monthly temperature data of **UKESM** model
~~~
cd ~/shared-tacco-ns1004k-cmip/MOHC/UKESM1-0-LL/historical/r1i1p1f2/Amon/ta/gn/v20190406/
ls
~~~
{: .language-bash}

~~~
ta_Amon_UKESM1-0-LL_historical_r1i1p1f2_gn_185001-194912.nc  
ta_Amon_UKESM1-0-LL_historical_r1i1p1f2_gn_195001-201412.nc
~~~
{: .output}

- To find historcal monthly zonal wind data of **NorESM** model
~~~
~/shared-tacco-ns1004k-cmroot/NorESM2-MM/historical/v20191108
ls *ua*Amon*
~~~
{: .language-bash}

~~~
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_185001-185912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_186001-186912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_187001-187912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_188001-188912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_189001-189912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_190001-190912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_191001-191912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_192001-192912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_193001-193912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_194001-194912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_195001-195912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_196001-196912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_197001-197912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_198001-198912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_199001-199912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_200001-200912.nc
ua_Amon_NorESM2-MM_historical_r1i1p1f1_gn_201001-201412.nc
~~~ 
{: .output}

## First practical: open a netCDF data file

<img src="../fig/practicals.jpg">

We do all the practicals at <font color="red">Jupyterhub</font>.  

*   [First look at a CMIP6 data file](#First-look-at-a-CMIP6-data-file)
	*   [What is a netCDF file](#What-is-a-netcdf-file?)
	*   [Inspect a netCDF file](#inspect-a-netcdf-file)

### First look at a CMIP6 data file

#### What is a netCDF file?

Netcdf stands for “network Common Data Form”. It is self-describing, portable, metadata friendly, supported by many languages
(including python, R, fortran, C/C++, Matlab, NCL, etc.), viewing tools (like panoply, ncview/ncdump) and tool suites of file operators (in particular NCO and CDO).

#### Inspect a netCDF file

NetCDF files are often too big to open directly (with your favorite text editor, for instance), however one can look at the **content** of a netCDF file instead, for example to *dump* the **header** of one of the netCDF history files.

<font color="red">Open a terminal at Jupyterhub:</font>

~~~
~/shared-tacco-ns1004k/SPARC
ncdump -h sparc.nc
~~~
{: .language-bash}

~~~
netcdf sparc {
dimensions:
        lev_wind = 46 ;
        lat = 41 ;
        month = 12 ;
        lev_temp = 33 ;
variables:
        float WIND(lev_wind, lat, month) ;
                WIND:units = "m/s" ;
                WIND:long_name = "SPARC: monthly wind climatologies" ;
                WIND:_FillValue = 1.e+36f ;
        float lev_wind(lev_wind) ;
                lev_wind:long_name = "pressure" ;
                lev_wind:units = "hPa" ;
        float lat(lat) ;
                lat:long_name = "latitude" ;
                lat:units = "degrees_north" ;
        int month(month) ;
                month:long_name = "month of year" ;
                month:info = "1=Jan, 2=Feb, ... , 12=Dec" ;
        float TEMP(lev_temp, lat, month) ;
                TEMP:units = "degK" ;
                TEMP:long_name = "SPARC: monthly temperature climatologies" ;
                TEMP:_FillValue = 1.e+36f ;
        float lev_temp(lev_temp) ;
                lev_temp:long_name = "pressure" ;
                lev_temp:units = "hPa" ;

// global attributes:
                :creation_date = "Tue Feb 21 09:23:03 CET 2017" ;
                :creator = "D. Shea, NCAR" ;
                :Conventions = "None" ;
                :referencese = "\n",
                        "Randel, W.J. et al., (2004)                                 \n",
                        "The SPARC Intercomparison of Middle Atmosphere Climatologies\n",
                        "J. Climate, 17, 986-1003                                    \n",
                        "doi:10.1175/1520-0442(2004)017<0986:TSIOMC>2.0.CO;2.        \n",
                        "                                                            \n",
                        "SPARC, 2002                                                 \n",
                        "SPARC Intercomparison of Middle Atmosphere Climatologies    \n",
                        "SPARC Report No. 3, Edited by W. Randel, M.-L. Chanin and C. Michaut, 96 pp.\n",
                        "" ;
                :WWW_data = "http://www.sparc-climate.org/data-center/data-access/reference-climatologies/randels-climatologies/temperature-wind-climatology/" ;
                :WWW = "http://www.sparc-climate.org/" ;
                :README = "ftp://sparc-ftp1.ceda.ac.uk/sparc/ref_clim/randel/temp_wind/README" ;
                :title = "SPARC Intercomparison of Middle Atmosphere Climatologies" ;
}
~~~
{: .output}

<!--
~~~
cd ~/shared-tacco-ns1004k-cmip/NCAR/CESM2-WACCM/historical/r1i1p1f1/Amon/ta/gn/v20190227
ncdump -h ta_Amon_CESM2-WACCM_historical_r1i1p1f1_gn_185001-201412.nc
~~~
{: .language-bash}

~~~
netcdf ta_Amon_CESM2-WACCM_historical_r1i1p1f1_gn_185001-201412 {
dimensions:
        lat = 192 ;
        plev = 19 ;
        nbnd = 2 ;
        lon = 288 ;
        time = UNLIMITED ; // (1980 currently)
variables:
        float ta(time, plev, lat, lon) ;
                ta:_FillValue = 1.e+20f ;
                ta:cell_measures = "area: areacella" ;
                ta:cell_methods = "time: mean" ;
                ta:comment = "Air Temperature" ;
                ta:coordinates = "time plev lat lon" ;
                ta:description = "Air Temperature" ;
                ta:frequency = "mon" ;
                ta:id = "ta" ;
                ta:long_name = "Air Temperature" ;
                ta:mipTable = "Amon" ;
                ta:missing_value = 1.e+20 ;
                ta:out_name = "ta" ;
                ta:prov = "Amon ((isd.003))" ;
                ta:realm = "atmos" ;
                ta:standard_name = "air_temperature" ;
                ta:time = "time" ;
                ta:time_label = "time-mean" ;
                ta:time_title = "Temporal mean" ;
                ta:title = "Air Temperature" ;
                ta:type = "real" ;
                ta:units = "K" ;
                ta:variable_id = "ta" ;
        double lat(lat) ;
                lat:axis = "Y" ;
                lat:bounds = "lat_bnds" ;
                lat:standard_name = "latitude" ;
                lat:title = "Latitude" ;
                lat:type = "double" ;
                lat:units = "degrees_north" ;
                lat:valid_max = 90. ;
                lat:valid_min = -90. ;
        double lon(lon) ;
                lon:axis = "X" ;
                lon:bounds = "lon_bnds" ;
                lon:standard_name = "longitude" ;
                lon:title = "Longitude" ;
                lon:type = "double" ;
                lon:units = "degrees_east" ;
                lon:valid_max = 360. ;
                lon:valid_min = 0. ;
        double plev(plev) ;
                plev:axis = "Z" ;
                plev:positive = "down" ;
                plev:requested = "100000. 92500. 85000. 70000. 60000. 50000. 40000. 30000. 25000. 20000. 15000. 10000. 7000. 5000. 3000. 2000. 1000. 500. 100." ;
                plev:standard_name = "air_pressure" ;
                plev:title = "pressure" ;
                plev:type = "double" ;
                plev:units = "Pa" ;
        double time(time) ;
                time:axis = "T" ;
                time:bounds = "time_bnds" ;
                time:standard_name = "time" ;
                time:title = "time" ;
                time:type = "double" ;
                time:units = "days since 0001-01-01 00:00:00" ;
                time:calendar = "noleap" ;
        double time_bnds(time, nbnd) ;
                time_bnds:calendar = "noleap" ;
                time_bnds:units = "days since 0001-01-01 00:00:00" ;
        float lat_bnds(lat, nbnd) ;
                lat_bnds:units = "degrees_north" ;
        float lon_bnds(lon, nbnd) ;
                lon_bnds:units = "degrees_east" ;

// global attributes:
                :Conventions = "CF-1.7 CMIP-6.2" ;
                :activity_id = "CMIP" ;
                :case_id = "4" ;
                :cesm_casename = "b.e21.BWHIST.f09_g17.CMIP6-historical-WACCM.001" ;
                :contact = "cesm_cmip6@ucar.edu" ;
                :creation_date = "2019-01-30T22:25:34Z" ;
                :data_specs_version = "01.00.29" ;
                :experiment = "all-forcing simulation of the recent past" ;
                :experiment_id = "historical" ;
                :external_variables = "areacella" ;
                :forcing_index = 1LL ;
                :frequency = "mon" ;
                :further_info_url = "https://furtherinfo.es-doc.org/CMIP6.NCAR.CESM2-WACCM.historical.none.r1i1p1f1" ;
                :grid = "native 0.9x1.25 finite volume grid (192x288 latxlon)" ;
                :grid_label = "gn" ;
                :initialization_index = 1LL ;
                :institution = "National Center for Atmospheric Research, Climate and Global Dynamics Laboratory, 1850 Table Mesa Drive, Boulder, CO 80305, USA" ;
                :institution_id = "NCAR" ;
                :license = "CMIP6 model data produced by <The National Center for Atmospheric Research> is licensed under a Creative Commons Attribution-[]ShareAlike 4.0 International License (https://creativecommons.org/licenses/). Consult https://pcmdi.llnl.gov/CMIP6/TermsOfUse for terms of use governing CMIP6 output, including citation requirements and proper acknowledgment. Further information about this data, including some limitations, can be found via the further_info_url (recorded as a global attribute in this file)[]. The data producers and data providers make no warranty, either express or implied, including, but not limited to, warranties of merchantability and fitness for a particular purpose. All liabilities arising from the supply of the information (including any liability arising in negligence) are excluded to the fullest extent permitted by law." ;
                :mip_era = "CMIP6" ;
                :model_doi_url = "https://doi.org/10.5065/D67H1H0V" ;
                :nominal_resolution = "100 km" ;
                :parent_activity_id = "CMIP" ;
                :parent_experiment_id = "piControl" ;
                :parent_mip_era = "CMIP6" ;
                :parent_source_id = "CESM2-WACCM" ;
                :parent_time_units = "days since 0001-01-01 00:00:00" ;
                :parent_variant_label = "r1i1p1f1" ;
                :physics_index = 1LL ;
                :product = "model-output" ;
                :realization_index = 1LL ;
                :realm = "atmos" ;
                :source = "CESM2 (2017): atmosphere: CAM6 (0.9x1.25 finite volume grid; 288 x 192 longitude/latitude; 70 levels; top level 4.5e-6 mb); ocean: POP2 (320x384 longitude/latitude; 60 levels; top grid cell 0-10 m); sea_ice: CICE5.1 (same grid as ocean); land: CLM5 0.9x1.25 finite volume grid; 288 x 192 longitude/latitude; 70 levels; top level 4.5e-6 mb); aerosol: MAM4 (0.9x1.25 finite volume grid; 288 x 192 longitude/latitude; 70 levels; top level 4.5e-6 mb); atmosChem: WACCM (0.9x1.25 finite volume grid; 288 x 192 longitude/latitude; 70 levels; top level 4.5e-6 mb; landIce: CISM2.1; ocnBgchem: MARBL (320x384 longitude/latitude; 60 levels; top grid cell 0-10 m)" ;
                :source_id = "CESM2-WACCM" ;
                :source_type = "AOGCM BGC CHEM AER" ;
                :sub_experiment = "none" ;
                :sub_experiment_id = "none" ;
                :table_id = "Amon" ;
                :tracking_id = "hdl:21.14100/6ca3c6f0-e925-4f46-aa8a-f83ebbc2c1ac" ;
                :variable_id = "ta" ;
                :variant_info = "CMIP6 CESM2 hindcast (1850-2014) with high-top atmosphere (WACCM6) with interactive chemistry (TSMLT1), interactive land (CLM5), coupled ocean (POP2) with biogeochemistry (MARBL), interactive sea ice (CICE5.1), and non-evolving land ice (CISM2.1)" ;
                :variant_label = "r1i1p1f1" ;
                :branch_time_in_parent = 20075. ;
                :branch_time_in_child = 674885. ;
                :branch_method = "standard" ;
}
~~~
{: .output}

~~~
cd ~/shared-tacco-ns1004k-cmip/MPI-M/MPI-ESM1-2-HR/historical/r1i1p1f1/Amon/ua/gn/v20190710
ncdump -h ua_Amon_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_201001-201412.nc
~~~
{: .language-bash}

~~~
netcdf ua_Amon_MPI-ESM1-2-HR_historical_r1i1p1f1_gn_201001-201412 {
dimensions:
        time = UNLIMITED ; // (60 currently)
        plev = 19 ;
        lat = 192 ;
        lon = 384 ;
        bnds = 2 ;
variables:
        double time(time) ;
                time:bounds = "time_bnds" ;
                time:units = "days since 1850-1-1 00:00:00" ;
                time:calendar = "proleptic_gregorian" ;
                time:axis = "T" ;
                time:long_name = "time" ;
                time:standard_name = "time" ;
        double time_bnds(time, bnds) ;
        double plev(plev) ;
                plev:units = "Pa" ;
                plev:axis = "Z" ;
                plev:positive = "down" ;
                plev:long_name = "pressure" ;
                plev:standard_name = "air_pressure" ;
        double lat(lat) ;
                lat:bounds = "lat_bnds" ;
                lat:units = "degrees_north" ;
                lat:axis = "Y" ;
                lat:long_name = "Latitude" ;
                lat:standard_name = "latitude" ;
        double lat_bnds(lat, bnds) ;
        double lon(lon) ;
                lon:bounds = "lon_bnds" ;
                lon:units = "degrees_east" ;
                lon:axis = "X" ;
                lon:long_name = "Longitude" ;
                lon:standard_name = "longitude" ;
        double lon_bnds(lon, bnds) ;
        float ua(time, plev, lat, lon) ;
                ua:standard_name = "eastward_wind" ;
                ua:long_name = "Eastward Wind" ;
                ua:comment = "Zonal wind (positive in a eastward direction)." ;
                ua:units = "m s-1" ;
                ua:cell_methods = "time: mean" ;
                ua:cell_measures = "area: areacella" ;
                ua:history = "2019-08-25T11:10:34Z altered by CMOR: Reordered dimensions, original order: time lat lon plev. 2019-08-25T11:10:34Z altered by CMOR: replaced missing value flag (-9e+33) and corresponding data with standard missing value (1e+20). 2019-08-25T11:10:34Z altered by CMOR: Inverted axis: lat." ;
                ua:missing_value = 1.e+20f ;
                ua:_FillValue = 1.e+20f ;

// global attributes:
                :Conventions = "CF-1.7 CMIP-6.2" ;
                :activity_id = "CMIP" ;
                :branch_method = "standard" ;
                :branch_time_in_child = 0. ;
                :branch_time_in_parent = 0. ;
                :contact = "cmip6-mpi-esm@dkrz.de" ;
                :creation_date = "2019-08-25T11:10:34Z" ;
                :data_specs_version = "01.00.30" ;
                :experiment = "all-forcing simulation of the recent past" ;
                :experiment_id = "historical" ;
                :external_variables = "areacella" ;
                :forcing_index = 1 ;
                :frequency = "mon" ;
                :further_info_url = "https://furtherinfo.es-doc.org/CMIP6.MPI-M.MPI-ESM1-2-HR.historical.none.r1i1p1f1" ;
                :grid = "gn" ;
                :grid_label = "gn" ;
                :history = "2019-08-25T11:10:34Z ; CMOR rewrote data to be consistent with CMIP6, CF-1.7 CMIP-6.2 and CF standards." ;
                :initialization_index = 1 ;
                :institution = "Max Planck Institute for Meteorology, Hamburg 20146, Germany" ;
                :institution_id = "MPI-M" ;
                :mip_era = "CMIP6" ;
                :nominal_resolution = "100 km" ;
                :parent_activity_id = "CMIP" ;
                :parent_experiment_id = "piControl" ;
                :parent_mip_era = "CMIP6" ;
                :parent_source_id = "MPI-ESM1-2-HR" ;
                :parent_time_units = "days since 1850-1-1 00:00:00" ;
                :parent_variant_label = "r1i1p1f1" ;
                :physics_index = 1 ;
                :product = "model-output" ;
                :project_id = "CMIP6" ;
                :realization_index = 1 ;
                :realm = "atmos" ;
                :references = "MPI-ESM: Mauritsen, T. et al. (2019), Developments in the MPI‐M Earth System Model version 1.2 (MPI‐ESM1.2) and Its Response to Increasing CO2, J. Adv. Model. Earth Syst.,11, 998-1038, doi:10.1029/2018MS001400,\n",
                        "Mueller, W.A. et al. (2018): A high‐resolution version of the Max Planck Institute Earth System Model MPI‐ESM1.2‐HR. J. Adv. Model. EarthSyst.,10,1383–1413, doi:10.1029/2017MS001217" ;
                :source = "MPI-ESM1.2-HR (2017): \n",
                        "aerosol: none, prescribed MACv2-SP\n",
                        "atmos: ECHAM6.3 (spectral T127; 384 x 192 longitude/latitude; 95 levels; top level 0.01 hPa)\n",
                        "atmosChem: none\n",
                        "land: JSBACH3.20\n",
                        "landIce: none/prescribed\n",
                        "ocean: MPIOM1.63 (tripolar TP04, approximately 0.4deg; 802 x 404 longitude/latitude; 40 levels; top grid cell 0-12 m)\n",
                        "ocnBgchem: HAMOCC6\n",
                        "seaIce: unnamed (thermodynamic (Semtner zero-layer) dynamic (Hibler 79) sea ice model)" ;
                :source_id = "MPI-ESM1-2-HR" ;
                :source_type = "AOGCM" ;
                :sub_experiment = "none" ;
                :sub_experiment_id = "none" ;
                :table_id = "Amon" ;
                :table_info = "Creation Date:(09 May 2019) MD5:e6ef8ececc8f338646ebfb3aeed36bfc" ;
                :title = "MPI-ESM1-2-HR output prepared for CMIP6" ;
                :variable_id = "ua" ;
                :variant_label = "r1i1p1f1" ;
                :license = "CMIP6 model data produced by MPI-M is licensed under a Creative Commons Attribution ShareAlike 4.0 International License (https://creativecommons.org/licenses). Consult https://pcmdi.llnl.gov/CMIP6/TermsOfUse for terms of use governing CMIP6 output, including citation requirements and proper acknowledgment. Further information about this data, including some limitations, can be found via the further_info_url (recorded as a global attribute in this file) and. The data producers and data providers make no warranty, either express or implied, including, but not limited to, warranties of merchantability and fitness for a particular purpose. All liabilities arising from the supply of the information (including any liability arising in negligence) are excluded to the fullest extent permitted by law." ;
                :cmor_version = "3.5.0" ;
                :tracking_id = "hdl:21.14100/92327739-2190-40af-87f9-f2dd927b60ae" ;
}
~~~
{: .output}

-->

{% include links.md %}
