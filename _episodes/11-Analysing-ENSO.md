---
title: "Model topic: ENSO"
teaching: 0
exercises: 0
questions:
- "How to analyze ENSO using CMIP6 data?"
objectives:
- "Learn about ENSO"
- "Learn to analyze CMIP6 data"
keypoints:
- "ENSO"
- "ONI"
- "SOI"
---

*   [Introduction](#introduction)
*   [Questions](#questions)
*   [Data](#data)
*   [Analysis](#analysis-indices)
	* [Niño regions](#niño-regions)
	* [ENSO indices](#enso-indices)
*   [References](#references)

# Introduction

- As one of the pronounced internal variability in the tropics, the [**El Niño-Southern Oscillation (ENSO)**](https://en.wikipedia.org/wiki/El_Ni%C3%B1o%E2%80%93Southern_Oscillation), can lead to pronounced changes in the atmospheric circulation and to surface climate on global scale.  
- El Niño–Southern Oscillation (ENSO) refers to an atmosphere-ocean phenomena ocurring over the tropical eastern Pacific Ocean in boreal winter with an irregular variation on a time scale of 2–7 years. 
- The **Southern Oscillation (SO)** refers the accompanying atmospheric part. 
- The ENSO warming phase of the sea temperature is known as El Niño (or ENSO positive phase) and the cooling phase as La Niña (or ENSO negative phase). 
- ENSO is an atmosphere-ocean coupled system, maintained by the Bjerknes feedback.
- Understanding how well state-of-the-art climate models capture the observed characteristics of ENSO and how it will change in the future are important for model evaluation and climate prediction.

*  <img src="../fig/enso-example.png"> 
Maps of sea surface temperature anomaly in the Pacific Ocean during a strong **La Niña** (top, December 1988) and **El Niño** (bottom, December 1997). Maps by NOAA Climate.gov

# Questions

- 1) Do CMIP6 models capture the observed ENSO characteristics?
- 2) How will ENSO change under global warming in CMIP6 simulations?

# Data

CMIP6 model data, observation-based ENSO indices (NCEP CPC)

# Analysis

## Niño regions

*  <img src="../fig/nino-regions.png">

There are several indices used to monitor the tropical Pacific, all of which are based on SST anomalies averaged across a given region as shown in the above figure. Usually the anomalies are computed relative to a base climatological period of 30 years. 

* [Nino regions and observed sea surface temperatures](https://www.ncdc.noaa.gov/teleconnections/enso/indicators/sst/#:~:text=El%20Ni%C3%B1o%20(La%20Ni%C3%B1a)%20is,C%20(%2D0.5%C2%B0C))

## ENSO indices

The **Oceanic Niño Index (ONI)** is NOAA's primary indicator for monitoring El Niño and La Niña.
The ONI tracks the running 3-month average sea surface temperature (SST) in the east-central tropical Pacific between 120°-170°W. Scientists call the area the Niño 3.4 region. A full-fledged El Niño or La Niña is indicated when the ONI exceed +0.5C or -0.5C for at least five consecutive months.  

* [Nino SST indices](https://climatedataguide.ucar.edu/climate-data/nino-sst-indices-nino-12-3-34-4-oni-and-tni)
* [ONI figure](https://www.climate.gov/news-features/understanding-climate/climate-variability-oceanic-nino-index)
* [ONI values](https://origin.cpc.ncep.noaa.gov/products/analysis_monitoring/ensostuff/ONI_v5.php)

The **Southern Oscillation Index (SOI)** is a standardized index based on the observed sea level pressure differences between Tahiti and Darwin, Australia.
*  <img src="../fig/SOI.png">

* [SOI index](https://www.ncdc.noaa.gov/teleconnections/enso/indicators/soi/)

# References

* Basic ENSO paper
* [Comparison of past and future ENSO simulations: Brown et al., 2020](https://cp.copernicus.org/articles/16/1777/2020/cp-16-1777-2020.pdf)
* [ENSO change under global warming: Fredriksen et al., 2020](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2020GL090640)

<!--  
(El Niño and La Niña events, ENSO SST and SLV patterns)
-->
 
{% include links.md %}
