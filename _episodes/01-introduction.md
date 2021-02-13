---
title: "Introduction on model"
teaching: 30
exercises: 0
questions:
- "What are CMIP6 climate models?"
objectives:
- "Learn about CMIP6 models"
- "Learn about CESM"
keypoints:
- "CMIP6"
---

<img src="https://github.com/MetOs-UiO/GEO4962/blob/gh-pages/fig/CMIP_logo_v4.jpg?raw=true" width="250"> | <img src="https://github.com/MetOs-UiO/GEO4962/blob/gh-pages/fig/CMIP6_MPIs.jpg?raw=true" width="250">

# CMIP6 - Coupled Model Intercomparison Project Phase 6

The Coupled Model Intercomparison Project (CMIP) organized under the auspices of the World Climate Research Programme’s (WCRP) Working Group on Coupled Modelling
(WGCM) started in 1995.The objective of CMIP is to better understand past, present, and future climate change arising from natural, unforced variability or in response to changes in radiative forcings in a multi-model context.  An important part of CMIP is to make the multi-model output publicly available in a standardized format for analysis by the wider climate community and users. The standardization of the model output in a specified format, and the collection, archival, and access of the model output through the Earth System Grid Federation (ESGF) data replication centres have facilitated multi-model analyses. 
CMIP6 is the undergoing phase started in 2015. 

*   [WCRP-WGCM: A Short Introduction to Climate Models - CMIP & CMIP6](https://www.wcrp-climate.org/wgcm-cmip)
*   [CMIP6-Endorsed MIPs overview](https://www.wcrp-climate.org/modelling-wgcm-mip-catalogue/modelling-wgcm-cmip6-endorsed-mips)
*   [ESGF CMPI6 data search and download portal](https://esgf-node.llnl.gov/search/cmip6/)
*   [CMIP6 overview paper: Eyring et al., 2016](https://gmd.copernicus.org/articles/9/1937/2016/gmd-9-1937-2016.html)
*   [CMIP6 scenario overview paper: O'Neill et al., 2016](https://gmd.copernicus.org/articles/9/3461/2016/gmd-9-3461-2016.pdf)


# CESM MODEL

*  <img src="../fig/img06.jpg">
*  <img src="../fig/cesm01.jpg">

The [Community Earth System Model](http://www.cesm.ucar.edu/) (CESM) is a fully-coupled, global climate model that provides state-of-the-art computer simulations of the Earth's past, present, and future climate states.

*   [CESM Web page](http://www.cesm.ucar.edu/)
*   [CESM User's Guide](https://escomp.github.io/CESM/release-cesm2/)
*   [CESM Supported Releases](https://csegweb.cgd.ucar.edu/experiments/public/)
*   [CESM scientifically validated configurations](http://www.cesm.ucar.edu/models/scientifically-supported.html)
*   [CESM Bulletin Board](http://bb.cgd.ucar.edu/)
*   [CESM Support Policy](http://www.cesm.ucar.edu/about/support.html)


## Community Atmosphere Model

*   [Community Atmosphere Model (CAM6, CAM-CHEM, WACCM)](https://github.com/ESCOMP/CAM/wiki)
*   [CAM-6 User's Guide](https://ncar.github.io/CAM/doc/build/html/users_guide/index.html)

* * *

## CAM 6 Source code overview

The full description of the Community Atmosphere Model CAM 6 can be found [here](https://ncar.github.io/CAM/doc/build/html/index.html).  

## CESM 

CESM is a fully-coupled, community, global climate model that provides state-of-the-art computer simulations of the Earth's past, present, and future climate states.  
Some facts about CESM:

*   Written in Fortran 90
*   About 900 000 lines of Fortran 90 code
*   About 12,000 lines of scripts that configure, build, and run the model
*   Parallelized with [MPI](http://www.mpi-forum.org/) (Message Passing Interface) and [OpenMP](http://openmp.org/) (Open Multi-Processing)
*   To keep track of code changes, CESM developers currently use [git](https://en.wikipedia.org/wiki/Git). 
*   Fortran Coding standard as well as style rules are enforced and anyone wishing to contribute to the Community Atmosphere Model must comply to these [contributing guidelines](https://github.com/ESCOMP/CAM/wiki).

To browse and explore CAM6 source code, you can look at [CAM github repository dev branch](https://github.com/ESCOMP/CAM/tree/cam_development).  

From a Linux terminal:

~~~ 
ssh -Y $LOGNAME@saga.sigma2.no
~~~ 
{: .language-bash}

where $LOGNAME is your UIO username (replace it by your own username!)  
Documentation on NIRD facility can be found [here](https://documentation.sigma2.no/storage/nird.html).  

The source code we will be using is stored (on Saga) in `/cluster/projects/nn1000k/cesm` and the cam component in `/cluster/projects/nn1000k/cesm/components/cam`:

~~~ 
module use /cluster/projects/nn1000k/modulefiles
module load cesm
cd $CESM_HOME/components/cam
ls 
~~~
{: .language-bash}



*   **bld**: scripts to generate makefiles and dependencies for compiling CAM6
*   **chem_proc**: MOZART [chemical preprocessor](http://www.cesm.ucar.edu/working_groups/Chemistry/chemistry.preprocessor.pdf)
*   **doc**: change log
*   **src**: source code for CAM6
*   **test**: CAM testing framework
*   **tools**: utility to generate or remap terrain dataset
*   **cime_config**: configuration for running CAM within CESM e.g. number of processors, etc.

The source code for CAM 6 is located in the "src" and its sub-directories (the main parts are highlighted in bold):

*   **control**: contains several Fortran 90 modules to control CAM 6\. That's a good starting point to explore CAM source code. Look for instance at cam_comp.F90:  
    The main subroutines for controlling CAM 6 are:

~~~    
        .
        .
        .
implicit none
private

public cam_init      ! First phase of CAM initialization
public cam_run1      ! CAM run method phase 1
public cam_run2      ! CAM run method phase 2
public cam_run3      ! CAM run method phase 3
public cam_run4      ! CAM run method phase 4
public cam_final     ! CAM Finalization

type(dyn_import_t) :: dyn_in   ! Dynamics import container
type(dyn_export_t) :: dyn_out  ! Dynamics export container

type(physics_state),       pointer :: phys_state(:) => null()
type(physics_tend ),       pointer :: phys_tend(:) => null()
type(physics_buffer_desc), pointer :: pbuf2d(:,:) => null()

real(r8) :: dtime_phys         ! Time step for physics tendencies.  Set by call to
                               ! stepon_run1, then passed to the phys_run*

!-----------------------------------------------------------------------
contains
!-----------------------------------------------------------------------

  subroutine cam_init( &
       caseid, ctitle, model_doi_url, &
       initial_run_in, restart_run_in, branch_run_in, &
       calendar, brnch_retain_casename, aqua_planet, &
       single_column, scmlat, scmlon,               &
       eccen, obliqr, lambm0, mvelpp,               &
       perpetual_run, perpetual_ymd, &
       dtime, start_ymd, start_tod, ref_ymd, ref_tod, &
       stop_ymd, stop_tod, curr_ymd, curr_tod, &
       cam_out, cam_in)
        .
        .
        .
~~~    
{: .language-bash}

*   **dynamics**: source code for the different dynamical core options.
*   **physics**: model physics (for instance check physics/cam directory)
*   **advection**
*   **chemistry**
*   Interaction with other components: one of these components will be used to interact with other models (land, etc.). We do not discuss this part as we do not run a full coupled configuration.

*   cpl: coupler for interactions between the different components.
*   utils: Fortran 90 modules containing utilities (such as sorting methods, namelist utilities, PIO io interface, etc.)
*   unit_drivers: Parallel Offline Radiation Tool (PORT); not used for our configuration.

{% include links.md %}

