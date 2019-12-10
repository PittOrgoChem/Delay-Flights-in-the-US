# DELAYED FLIGHTS IN THE US: A Painful Reality 

This work is inspired by a recent event that almost ruined a pleasant long weekdend in San Juan, Puerto Rico. What started as a fun trip to this beatiful island, slowly changed into a very painful experience for my family. A flight that was supposed to leave at 8:30 PM in the evening ended up leaving at 2:30 AM. The long wait was horrific, 2 hours inside a plane without A/C probably resembled more a torture than a pleasure. Since my intention is not to bore you with a story that may be millions can share, I decided to know a little bit more about the behind-the-scenes of flight delays

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
## Data

A master dataset comprising flight delay information exclusive for the United States during the period of 2014-2018, was assembled after manually downloading the corresponding files from the United States Department of Transportation website (Bureau of Transportation Statistics, https://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp?pn=1). After storing each separate file in a working directory, a list of files was created and a loop used to read and append the data to a dataframe named 'df_master'. The raw data is presented aggregated by year, month, airline/carrier, and airport, and other feautures related to flight operations, cancellations, and delays. A more detailed description of the available features is presented below:

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

## References

- The original data used for this work was manually downloaded from the United States Department of Transportation website hosted under the following link: https://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp?pn=1.
- Appropriate description of the original fields can be found in https://www.bts.gov/topics/airlines-and-airports/understanding-reporting-causes-flight-delays-and-cancellations
- The documentation available for the Python's libraries used in this work and certain built-in functions and methods was accessed through the internet for reference
