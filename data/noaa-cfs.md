# NOAA Climate Forecast System (CFS)

## Overview

The NOAA [Climate Forecast System](https://cfs.ncep.noaa.gov/) (CFS) is a model representing the global interaction between Earth's oceans, land, and atmosphere. Produced under guidance from the National Centers for Environmental Prediction (NCEP), this model offers hourly data with a horizontal resolution down to one-half of a degree (approximately 56 km) around Earth for many variables. CFS assimilates observations from data sources including surface observations, upper air balloon observations, aircraft observations, and satellite observations.

Data are retained for 30 days.

This dataset is available on Azure thanks to the [NOAA Big Data Program](https://www.noaa.gov/organization/information-technology/big-data-program).


## Storage resources

Data are stored in [GRIB](https://en.wikipedia.org/wiki/GRIB) format as blobs in the East US Azure region, in the following blob container:

`https://noaacfs.blob.core.windows.net/cfs`

Forecasts are updated every six hours.  Within the above container, each forecast is available in a folder named:

`cfs.yyyymmdd/hh`

* yyyymmdd is the year, month, and day
* hh is the six-hourly forecast cycle, one of 00, 06, 12, or 18

Each forecast cycle folder contains nine subfolders:

* 6hrly_grib_[01,02,03,04]
* time_grib_[01,02,03,04]
* monthly_grib_01

01, 02, 03, and 04 indicate an ensemble member.

All subfolders will make use of the following variables in filenames:

* FLXF (surface, radiative fluxes)
* PGBF (3D pressure level, 1-degree resolution)
* OCNH (3D ocean data, 0.5-degree resolution)
* OCNF (3D ocean data, 1-degree resolution)
* IPVF (3D isentropic level data, 1-degree resolution)

File naming convention variables among the three subfolder types.


### `6hrly` subfolders

Within each "6hrly" subfolder, data are named according to:

`[variable][YYYYMMDD].[ensemble-member].[yyyymmddhh].grb2`

* YYYYMMDDHH is the forecast hour.
* yyyymmddhh is the initial hour of the forecast cycle.
* [ensemble-member] is the ensemble member, and will always match the containing folder

For example, this file:

https://noaacfs.blob.core.windows.net/cfs/cfs.20210821/12/6hrly_grib_01/flxf2021101106.01.2021082112.grb2

...contains six-hourly surface/flux information predicted for 2021.10.11:06:00, generated at 2021.08.21:12:00.


### `monthly` subfolder

Within each "monthly" subfolder, data are named according to:

`[variable].[ensemble-member].[yyyymmddhh].[YYMM].avrg.grib.[NN]z.grb2`

* [ensemble-member] is always 01 for monthly data
* yyyymmddhh is the initial hour of the forecast cycle.
* YYMM is the forecast month

For example, this file:

https://noaacfs.blob.core.windows.net/cfs/cfs.20210821/00/monthly_grib_01/flxf.01.2021082100.202109.avrg.grib.grb2

...contains surface/flux information predicted for the month 2021.09, generated at 2021.08.21:00:00.


### `time` subfolders

Documentation pending.


## Region information

Large-scale processing is best performed in the East US Azure region, where the data are stored.  If you are using RAP data for environmental science applications, consider applying for an [AI for Earth grant](http://aka.ms/ai4egrants) to support your compute requirements.


## Mounting the container

We also provide a read-only SAS (shared access signature) token to allow access via, e.g., [BlobFuse](https://github.com/Azure/azure-storage-fuse), which allows you to mount blob containers as drives:

`https://noaacfs.blob.core.windows.net/cfs?sv=2020-08-04&si=cfs-ro&sr=c&sig=SiyDg5niMXyIZ3583DYW4o7xNRe9HUJhAIzFgCoiUnc%3D`

Mounting instructions for Linux are [here](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-how-to-mount-container-linux).


## Contact

For questions, please contact the NOAA Big Data Program Team at [`noaa.bdp@noaa.gov`](mailto:noaa.bdp@noaa.gov?subject=azure%20cfs%20question).


## Notices

Microsoft provides this dataset on an "as is" basis.  Microsoft makes no warranties (express or implied), guarantees, or conditions with respect to your use of the dataset.  To the extent permitted under your local law, Microsoft disclaims all liability for any damages or losses - including direct, consequential, special, indirect, incidental, or punitive - resulting from your use of this dataset.  This dataset is provided under the original terms that Microsoft received source data.