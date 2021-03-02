---
title: "Introduction on model"
teaching: 30
exercises: 0
questions:
- "What are CMIP6 climate models?"
objectives:
- "Learn about CMIP6 models"
- "Learn about CESM，MPI-ESM, NorESM"
keypoints:
- "CMIP6"
- "CESM"
- "MPI-ESM"
- "NorESM"
---

*  <img src="https://github.com/MetOs-UiO/GEO4962/blob/gh-pages/fig/CMIP_logo_v4.png" width="500">
*  <img src="https://github.com/MetOs-UiO/GEO4962/blob/gh-pages/fig/CMIP6_MIPs.jpg" width="500">

# CMIP6 - Coupled Model Intercomparison Project Phase 6

The Coupled Model Intercomparison Project (CMIP) organized under the auspices of the World Climate Research Programme’s (WCRP) Working Group on Coupled Modelling
(WGCM) started in 1995.The objective of CMIP is to better understand past, present, and future climate change arising from natural, unforced variability or in response to changes in radiative forcings in a multi-model context.  An important part of CMIP is to make the multi-model output publicly available in a standardized format for analysis by the wider climate community and users. The standardization of the model output in a specified format, and the collection, archival, and access of the model output through the Earth System Grid Federation (ESGF) data replication centres have facilitated multi-model analyses. 
CMIP6 is the undergoing phase started in 2015. 

    Website links
*   [WCRP-WGCM: A Short Introduction to Climate Models - CMIP & CMIP6](https://www.wcrp-climate.org/wgcm-cmip)
*   [CMIP6-Endorsed MIPs overview](https://www.wcrp-climate.org/modelling-wgcm-mip-catalogue/modelling-wgcm-cmip6-endorsed-mips)
*   [ESGF CMPI6 data search and download portal](https://esgf-node.llnl.gov/search/cmip6/)
*   [CMIP6 data request home page](http://clipc-services.ceda.ac.uk/dreq/index.html)
*   [CMIP6 data frenquency list](http://clipc-services.ceda.ac.uk/dreq/index/miptable.html)
*   [CMIP6 variables list](http://clipc-services.ceda.ac.uk/dreq/index/var.html)
    Paper links
*   [CMIP6 overview paper: Eyring et al., 2016](https://gmd.copernicus.org/articles/9/1937/2016/gmd-9-1937-2016.html)
*   [CMIP6 scenario overview paper: O'Neill et al., 2016](https://gmd.copernicus.org/articles/9/3461/2016/gmd-9-3461-2016.pdf)
*   [CMIP6 data request overview paper](https://gmd.copernicus.org/articles/13/201/2020/)

# CESM

*  <img src="../fig/cesm01.jpg">

The [Community Earth System Model](http://www.cesm.ucar.edu/) (CESM) is a fully-coupled, community, global climate model that provides state-of-the-art computer simulations of the Earth's past, present, and future climate states.

Some facts about CESM:

*   Written in Fortran 90
*   About 900 000 lines of Fortran 90 code
*   About 12,000 lines of scripts that configure, build, and run the model
*   Parallelized with [MPI](http://www.mpi-forum.org/) (Message Passing Interface) and [OpenMP](http://openmp.org/) (Open Multi-Processing)
*   To keep track of code changes, CESM developers currently use [git](https://en.wikipedia.org/wiki/Git). 
*   Fortran Coding standard as well as style rules are enforced and anyone wishing to contribute to the Community Atmosphere Model must comply to these [contributing guidelines](https://github.com/ESCOMP/CAM/wiki).

*   [CESM Web page](http://www.cesm.ucar.edu/)
*   [CESM User's Guide](https://escomp.github.io/CESM/release-cesm2/)
*   [CESM Supported Releases](https://csegweb.cgd.ucar.edu/experiments/public/)
*   [CESM scientifically validated configurations](http://www.cesm.ucar.edu/models/scientifically-supported.html)
*   [CESM Bulletin Board](http://bb.cgd.ucar.edu/)
*   [CESM Support Policy](http://www.cesm.ucar.edu/about/support.html)

## CAM6

The 6th phase of the Community Atmosphere Model (CAM6) is the atmospheric component of the CESM used in CMIP6. The full description of the CAM6 can be found [here](https://ncar.github.io/CAM/doc/build/html/index.html).  

*   [Community Atmosphere Model (CAM6, CAM-CHEM, WACCM)](https://github.com/ESCOMP/CAM/wiki)
*   [CAM-6 User's Guide](https://ncar.github.io/CAM/doc/build/html/users_guide/index.html)

* * *

## WACCM6


# MPI-ESM

# NorESM

The [Norwegian Earth System Model](https://www.noresm.org/) (NorESM) has been developed since 2007 and has been an important tool for Norwegian climate researchers in the study of the past, present and future climate. 

The further development of NorESM will be supported by the [Infrastructure for Norwegian Earth System Modeling](https://www.ines.noresm.org/)(INES)  project.  

*   [NorESM Web page](https://www.noresm.org/)
*   [NorESM code access](https://github.com/NorESMhub/NorESM)
*   [NorESM-1 documentation](https://noresm-docs.readthedocs.io/en/noresm1/)
*   [NorESM-2 documentation](https://noresm-docs.readthedocs.io/en/noresm2/)


{% include links.md %}

