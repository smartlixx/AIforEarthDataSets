# NOAA Integrated Surface Data (ISD)

## Overview

The NOAA [Integrated Surface Database](https://www.ncei.noaa.gov/products/land-based-station/integrated-surface-database) (ISD) is a global database that consists of hourly and synoptic surface observations compiled from numerous sources into a common format and data model. The database incorporates data from over 35,000 stations around the world, and includes observations data from as far back as 1901. There are currently more than 14,000 active ISD stations that are updated daily in the database.

ISD includes numerous parameters such as wind speed and direction, wind gust, temperature, dew point, cloud data, sea level pressure, altimeter setting, station pressure, present weather, visibility, precipitation amounts for various time periods, and snow depth.

This dataset is available on Azure thanks to the [NOAA Big Data Program](https://www.noaa.gov/organization/information-technology/big-data-program).


## Storage resources

Data are stored in the following blob container in the West Europe Azure region:

`https://noaaisd.blob.core.windows.net/noaa-isd`

Detailed documentation is pending.


## Region information

Large-scale processing is best performed in the West Europe Azure region, where the data are stored.  If you are using this data for environmental science applications, consider applying for an [AI for Earth grant](http://aka.ms/ai4egrants) to support your compute requirements.


## Contact

For any data delivery issues or any questions in general, please contact the NOAA Big Data Program Team at [`noaa.bdp@noaa.gov`](mailto:noaa.bdp@noaa.gov?subject=azure%20rap%20question).


## Notices

Microsoft provides this dataset on an "as is" basis.  Microsoft makes no warranties (express or implied), guarantees, or conditions with respect to your use of the dataset.  To the extent permitted under your local law, Microsoft disclaims all liability for any damages or losses - including direct, consequential, special, indirect, incidental, or punitive - resulting from your use of this dataset.  This dataset is provided under the original terms that Microsoft received source data.