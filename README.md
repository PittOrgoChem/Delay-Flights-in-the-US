# DELAYED FLIGHTS IN THE US: A Painful Reality 

## Project Motivation

This work is inspired by a recent event that almost ruined a pleasant long weekdend in San Juan, Puerto Rico after a very long flight delay. On my return I decided to gather some data from public sources (see below) and use some basic data analysis and visualization to understand more in depth the dynamics of flight delays in the United States in the last 5 years (2014-2018). The following three main questions were employed to drive the analysis and the answers to them are briefly stated below:

1. What are the most common factors causing delays in flights in the United States during 2014-2018 period?

2. What airlines reported the highest incidence of flight delays during the 2014-2018 period?

3. Was the size of the airline (number of operated flights) related to the incidence of flight delays during the specified period?

## Requirements
The following list of Python packages were employed during the project to handle, clean, and organize the data as well as to create visualization

```
import numpy as np
import pandas as pd
import seaborn as sns
import os, fnmatch
import matplotlib.pyplot as plt
from matplotlib import rcParams
rcParams.update({'figure.autolayout': True})
%matplotlib inline
```
## File Descriptions

The corresponding files can be found in this repository along with the Jupyter Notebook containing all the code employed to transform and analyze the data. The .csv files contain information about flight delays in the United States aggregated by year, month, airline/carrier, and airport. The list below gives the dimensions of each of the files mentioned.

- 2014.csv: 13980 rows and 22 columns
- 2015.csv: 13528 rows and 22 columns
- 2016.csv: 12217 rows and 22 columns
- 2017.csv: 12518 rows and 22 columns
- 2018.csv: 20231 rows and 22 columns
- delayed_flights.ipynb: Jupyter Notebook containing code and analysis

## Data

A master dataset comprising flight delay information exclusive for the United States during the period of 2014-2018, was assembled after manually downloading the corresponding files from the United States Department of Transportation website (Bureau of Transportation Statistics, https://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp?pn=1). 

After storing each separate file in a working directory, a list of files was created and a loop used to read and append the data to a dataframe named 'df_master'. The raw data is presented aggregated by year, month, airline/carrier, and airport, and other feautures related to flight operations, cancellations, and delays. A more detailed description of the available features is presented below:

- 'year': year
- 'month': month
- 'carrier_name: name of the airline/carrier
- 'airport': airport code or abbreviation
- 'airport_name': full name of the airport, including city and state
- 'total_flights': total number of flights operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'delayed_flights': total number of delayed flights operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'del_carrier_ct': total number of delayed flights DUE TO CARRIER, operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'del_weather_ct': total number of delayed flights DUE TO WEATHER, operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'del_nas_ct': total number of delayed flights DUE TO NATIONAL AVIATION SYSTEM (NAS), operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'del_security_ct': total number of delayed flights DUE TO SECURITY, operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'del_late_aircraft_ct': total number of delayed flights DUE TO LATE AIRCRAFT, operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'cancelled_flights': total number of CANCELLED operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'diverted_flights': total number of DIVERTED operated by the specific carrier during the specified 'year' and 'month' at a specified airport
- 'tot_min_delay': total combined MINUTES DELAYED by flights operated a the specific carrier during the specified 'year' and 'month' at a specified airport
- 'min_carrier_delay': total combined MINUTES DELAYED due to CARRIER by flights operated a the specific carrier during the specified 'year' and 'month' at a specified airport
- 'min_weather_delay': total combined MINUTES DELAYED due to WEATHER by flights operated a the specific carrier during the specified 'year' and 'month' at a specified airport
- 'min_nas_delay': total combined MINUTES DELAYED due to NAS by flights operated a the specific carrier during the specified 'year' and 'month' at a specified airport
- 'min_security_delay': total combined MINUTES DELAYED due to SECURITY by flights operated a the specific carrier during the specified 'year' and 'month' at a specified airport
- 'min_late_aircraft_delay': total combined MINUTES DELAYED due to LATE AIRCRAFT by flights operated a the specific carrier during the specified 'year' and 'month' at a specified airport

Appropriate description of the original fields present in the raw dataset can be found in https://www.bts.gov/topics/airlines-and-airports/understanding-reporting-causes-flight-delays-and-cancellations

Other features were engineered during the course of the project to provide better comparisons across airlines and airports with different sizes of operations. A list of these features and a brief description is presented as follows:

- 'state': state where specific airport is located
- 'pct_delayed_flights': percentage of DELAYED flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_cancelled_flights': percentage of CANCELLED flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_diverted_flights': percentage of DIVERTED flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_del_carrier': percentage of DELAYED DUE TO CARRIER flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_del_weather': percentage of DELAYED DUE TO WEATHER flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_del_nas': percentage of DELAYED DUE TO NAS flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_del_security': percentage of DELAYED DUE TO SECURITY flights operated by a specific airline during a specific year and month at a specific airport
- 'pct_del_late': percentage of DELAYED DUE TO LATE AIRCRAFT flights operated by a specific airline during a specific year and month at a specific airport
- 'min_per_delay': average DELAY DURATION by a specific airline during a specific year and month at a specific airport

Other features were created transiently to aid in the preparation of visualization and more details are offered in the Jupyter Notebook available in this repository.

## Summary of Findings

**Question #1:**
  Through this question, the intention was to elucidate the most common reasons behind delayed flights in the US as categorized by the US Department of Transportation. Delays due to **CARRIER** were found to be the most common on average

**Question #2:**
  In this section, the intention was to get a deeper look into each airline that operated in the US during the period 2014-2018 in terms of delays and their causes. The findings were summarized in a visualization that compares the performance of each airline in terms of percentage of delay flights during the period specified.
  
**Question #3:**
  The question above, demanded an evaluation of a possible relationship between the size of the operations of the airlines included in the study and the percentage of delayed flights during the specified period. No relationship was found between the two variables, since large and small size airlines performed very similar on average.
  
For more details about this observations, visit the [post](https://medium.com/@jeanpitteloud/delayed-flights-in-the-us-6a25e05cf5c2) on Medium.

## Licensing, Authors, Acknowledgements

- The original data used for this work was manually downloaded from the United States Department of Transportation website hosted under the following link: https://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp?pn=1.
- Appropriate description of the original fields can be found in https://www.bts.gov/topics/airlines-and-airports/understanding-reporting-causes-flight-delays-and-cancellations.
- The documentation available for the Python's libraries used in this work and certain built-in functions and methods was accessed through the internet for reference.
