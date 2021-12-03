# Data Notes
==============

<img
  src="https://www.cascobayestuary.org/wp-content/uploads/2014/04/logo_sm.jpg"
  style="position:absolute;top:10px;right:50px;" />
  
All data was sourced from the "Data" folder from the "LCWMD_Monitoring"
GitHub archive from the 2020 State of Casco Bay Report 
(https://github.com/CBEP-SoCB/LCWMD_Monitoring_sum).  Additional metadata on the
contents of these files is available there.

## Data Files in This Folder
1.  **Daily_Data.csv**   -- Daily summaries (min, max, median, mean, sd, IQr, n)
    derived from *Sonde_Data.csv*. See related code in 
    *Make_Daily_Summaries.Rmd* for details.  
2.  **Exceeds_Data.csv**  -- Data derived from *Daily_Data.csv* containing flags
    that indicate whether conditions that day exceeded acute or chronic exposure
    thresholds.   Thresholds for Chlorides, DO, and Percent Saturation are
    derived from Maine water quality criteria.  Temperature thresholds are
    derived from a study of brook trout habitat use in the upper midwest.  See
    the code in *Make_Daily_Summaries.Rmd* for threshold values and other
    details.  
3.  **Full_Data.csv** -- Data derived from *Daily_data.csv* containing lags and
    weighted sums for time series analysis.  The data contains missing values
    where there are gaps in the data, so that autocorrelation-based regression
    models rely only on data where lag data are available.  See the code in
    *Make_Complete_Data.Rmd* for details.  
4.  **Portland_Jetport_2009-2019_Long.csv**  --   Weather data downloaded from
    the NOAA API using the program "noaaweatherdataGUI.py".  We downloaded data 
    anew, because a programming error that did not properly account for changes 
    in integer arithmetic  converting from python 2 to python 3 led to the
    downloaded data omitting February 29th in leap years.  Another programming
    error sometimes lead to misalignment of data columns, which can be avoided 
    by reading in long-form data.
