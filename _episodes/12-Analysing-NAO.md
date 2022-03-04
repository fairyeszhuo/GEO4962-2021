---
title: "Model topic: The North Atlantic Oscillation (NAO)"
teaching: 0
exercises: 0
questions:
- "How to analyze NAO using CMIP6 data?"
objectives:
- "Learn about NAO"
- "Learn to analyze CMIP6 data"
keypoints:
- "NAO"
---


*   [Introduction](#introduction)
*   [Questions](#research-question-ideas)
*   [Data](#data)
*   [References](#references)


# Introduction
## NAO
The NAO is the dominant atmospheric circulation pattern over the North Atlantic/Europe in winter-spring.
<center>
  
![image](https://user-images.githubusercontent.com/44640857/111969377-74be0780-8afa-11eb-8ce8-4e0a45d9147f.png) 
  
[*NCEP CPC*](https://www.cpc.ncep.noaa.gov/products/precip/CWlink/pna/JFM_season_nao_index.shtml)
 
</center>
- How to calculate the NAO index: [NCEP CPC NAO indices](https://www.cpc.ncep.noaa.gov/products/precip/CWlink/daily_ao_index/history/method.shtml), [UCAR Hurrell station-based NAO index](https://climatedataguide.ucar.edu/climate-data/hurrell-north-atlantic-oscillation-nao-index-station-based), [UCAR Hurrell PC-based NAO index](https://climatedataguide.ucar.edu/climate-data/hurrell-north-atlantic-oscillation-nao-index-pc-based)
<!-- [Python package for eof analysis](https://ajdawson.github.io/eofs/latest/api/eofs.xarray.html) -->
- Stratospheric impact on the NAO: 
<center>
![image](https://user-images.githubusercontent.com/44640857/111969057-21e45000-8afa-11eb-8dc9-d39f98806c49.png)
  
[*Scaife et al., 2005*](https://agupubs.onlinelibrary.wiley.com/doi/epdf/10.1029/2005GL023226)
  
</center>


# Research question ideas
- How is the frequancy and strength of NAO in CMIP6 models? 
- How does it compare with observations? 
- Are the impacts on surface climate captured in the models?
- How is the NAO likely to change in a future climate? Under extreme climate change? 

# Data
- CMIP6 model data: monthly mean sea level pressure; geopotential height; temperature at surface, 500 hPa, and 50 hPa; precipitation
- CMIP6 experiments: historical, SSP585, piControl, abrupt-4xCO2
- Observations: [NCEP CPC data](https://www.cpc.ncep.noaa.gov/products/precip/CWlink/pna/nao.shtml), [NCDC NOAA figure and data](https://www.ncdc.noaa.gov/teleconnections/nao/)


# References
- Lecture slides and material
- [NCEP CPC NAO](https://www.cpc.ncep.noaa.gov/products/precip/CWlink/pna/nao.shtml)
- [A stratospheric influence on the winter NAO and North Atlantic surface climate: Scaife et al., 2005](https://agupubs.onlinelibrary.wiley.com/doi/epdf/10.1029/2005GL023226)
- NAO and its relationship with the Northern Hemisphere mean surface temperature in CMIP5 simulations: [Wang et al., 2017](https://doi.org/10.1002/2016JD025979)

{% include links.md %}
