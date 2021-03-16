# NOAA Rapid Refresh (RAP)

## Overview

The NOAAA [Rapid Refresh](https://www.nco.ncep.noaa.gov/pmb/products/rap/) (RAP) is a NOAA/NCEP operational weather prediction system comprised primarily of a numerical forecast model and analysis/assimilation system to initialize that model. It covers North America and is run with a horizontal resolution of 13 km and 50 vertical layers. The RAP was developed to serve users needing frequently updated short-range weather forecasts, including those in the US aviation community and US severe weather forecasting community. The model is run for every hour of the day; it is integrated to 51 hours for the 03/09/15/21 UTC cycles and to 21 hours for every other cycle. The RAP uses the ARW core of the [WRF model](https://www.mmm.ucar.edu/weather-research-and-forecasting-model) and the [Gridpoint Statistical Interpolation](https://ral.ucar.edu/solutions/products/gridpoint-statistical-interpolation-gsi) (GSI) analysis.  The analysis is aided with the assimilation of cloud and hydrometer data to improve short-range cloud and precipitation forecasts.

This dataset is available on Azure thanks to the [NOAA Big Data Program](https://www.noaa.gov/organization/information-technology/big-data-program).


## Storage resources

Data are stored in [GRIB](https://en.wikipedia.org/wiki/GRIB) format.

GRIB files are stored as blobs in the East US Azure region, in the following blob container:

`https://noaarap.blob.core.windows.net/rap`

Within that container, files are named as:

`rap.[year][month][day]/[product][year][month][day]/rap.t[CC]z.[parameter]f[FF].grib2`

* `year` is a four-digit year
* `month` is a two-digit month
* `day` is a two-digit day
* `CC` is the cycle run
* `parameter` is the RAP parameter (e.g. awip32)
* `FF` represents the forecast hour

For example, for the file:

`rap.20210315/rap.t00z.awip32f00.grib2`

* Year: 2021
* Month: 03
* Day: 15
* CC (cycle run): 00
* Parameter: awip32
* FF (forecast hour): 00


## Region information

Large-scale processing is best performed in the East US Azure region, where the data are stored.  If you are using RAP data for environmental science applications, consider applying for an [AI for Earth grant](http://aka.ms/ai4egrants) to support your compute requirements.


## Mounting the container

We also provide a read-only SAS (shared access signature) token to allow access via, e.g., [BlobFuse](https://github.com/Azure/azure-storage-fuse), which allows you to mount blob containers as drives:

`https://noaarap.blob.core.windows.net/rap?sv=2020-04-08&si=rap-ro&sr=c&sig=2Fkgr%2BmCJZ%2BKL39jzhWDUVryVyx977HFeKsAmVRU7P8%3D`

Mounting instructions for Linux are [here](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-how-to-mount-container-linux).


## Contact

For any data delivery issues or any questions in general, please contact the NOAA Big Data Program Team at [`noaa.bdp@noaa.gov`](mailto:noaa.bdp@noaa.gov?subject=azure%20rap%20question).


## Notices

MICROSOFT PROVIDES AZURE OPEN DATASETS ON AN "AS IS" BASIS. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, GUARANTEES OR CONDITIONS WITH RESPECT TO YOUR USE OF THE DATASETS. TO THE EXTENT PERMITTED UNDER YOUR LOCAL LAW, MICROSOFT DISCLAIMS ALL LIABILITY FOR ANY DAMAGES OR LOSSES, INCLUDING DIRECT, CONSEQUENTIAL, SPECIAL, INDIRECT, INCIDENTAL OR PUNITIVE, RESULTING FROM YOUR USE OF THE DATASETS. 

This dataset is provided under the original terms that Microsoft received source data. The dataset may include data sourced from Microsoft. 

