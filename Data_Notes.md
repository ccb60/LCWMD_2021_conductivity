# Data Notes
==============

<img
  src="https://www.cascobayestuary.org/wp-content/uploads/2014/04/logo_sm.jpg"
  style="position:absolute;top:10px;right:50px;" />
  
All data was sourced from the "Derived_Data" folder from the "LCWMD_Monitoring" GitHub archive from the 2020 State of Casco Bay (https://github.com/ccb60/LCWMD_Monitoring)

## Data Files in This Folder
1.  **Sonde_Data.csv**  --  (Omitted from Github Repository because of its size)
    Contains raw data assembled from original Excel files.  See code in 
    *Import_Data.Rmd*  for details.  
2.  **Daily_Data.csv**   -- Daily summaries (min, max, median, mean, sd, IQr, n)
    derived from *Sonde_Data.csv*. See related code in 
    *Make_Daily_Summaries.Rmd* for details.  
3.  **Exceeds_Data.csv**  -- Data derived from *Daily_Data.csv* containing flags
    that indicate whether conditions that day exceeded acute or chronic exposure
    thresholds.   Thresholds for Chlorides, DO, and Percent Saturation are
    derived from Maine water quality criteria.  Temperature thresholds are
    derived from a study of brook trout habitat use in the upper midwest.  See
    the code in *Make_Daily_Summaries.Rmd* for threshold values and other
    details.  
4.  **Full_Data.csv** -- Data derived from *Daily_data.csv* containing lags and
    weighted sums for time series analysis.  The data contains missing values
    where there are gaps in the data, so that autocorrelation-based regression
    models rely only on data where lag data are available.  See the code in
    *Make_Complete_Data.Rmd* for details.  
5.  **Portland_Jetport_2009-2019_Long.csv**  --   Weather data downloaded from
    the NOAA API using the program "noaaweatherdataGUI.py".  We downloaded data 
    anew, because a programming error that did not properly account for changes 
    in integer arithmetic  converting from python 2 to python 3 led to the
    downloaded data omitting February 29th in leap years.  Another programming
    error sometimes lead to misalignment of data columns, which can be avoided 
    by reading in long-form data.

## Data omitted from this folder
The LCWMD sonde data, with data collected generally every fifteen minutes to
half an hour across multiple sites, amounts to a substantial amount of data. In
order to reduce the size of this Archive, we have omitted some intermediate
data.

In particular, we  omitted:

-  **Sonde_Data.csv** which is about 54 MB in size.  This is an aggregated and
   simplified version of the raw sonde data received from GZA, and included in
   the folder "Original_Data". If you need this file, you can generate it by
   downloading the archive and running "Import_Data.Rmd".
