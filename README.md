This script was developed using Chapter 7 (Julian Day), Chapter 50 (Perigee and Apogee of the Moon), and Chapter 10 (Dynamical and Universal Time) of Jean Meesus' Astronomical Algorithms. 
Final times are given in UT, which is within .9 seconds of UTC. This is described in further detail on one of NASA's solar eclipse [webpages](https://eclipse.gsfc.nasa.gov/SEhelp/TimeZone.html).
To convert times and dates to EST, final printed dates should be offset 4 or 5 hours back, depending on time of year. 
Script requires input of specific time of year (year as an integer and month as a fraction) to indicate when perigee occurs. 
Year values must be in the form "year.month" where month is in fraction of year. For example, the end of April in 2041 would be 2041.33. 


The script incorporates use of a csv file (NCKT_tabulated_t_values) to iterate through the year and display all the lunar perigees for a requested year. These t values were generated by dividing 1 by 36, 
and multiplying by successive integers 1-36 in order to include each part of the year. When added to the desired year, these t values give the specific month (beginning, middle, and end) 
to be tested for lunar perigee. For example, to find the lunar perigee for the cycle in January, the t values used would be 0, 0.0278, and 0.0556.
These values, when added to the year in question, would test for perigee at the beginning, middle, and end of January. By repeating this process for each month and removing repeated perigees, we can generate
a list of pergiees for the whole year and account for months when a perigee might occur twice (for example, if a perigee occurs at the beginning and end of a month based on length of the lunar cycle), or if
testing the end of one month yields the same perigee as the beginning of another, if the dates are within the same lunar cycle. This way, only the desired year needs to be input to show all perigees for the year.


Repeated lunar perigees can also occur when a generated k value is the same for two t values, 
since k is either rounded up or down to the nearest integer or to the nearest 0.5 value. 

The relevant code to be run can be found in the Lunar Perigee Calculation cell of the [NCKT Lunar Perigee Calculations Jupyter Notebook](https://github.com/Perri-Woodard/NC-King-Tides/blob/main/NCKT%20Lunar%20Perigee%20Calculations.ipynb). The Apogee Calculation cell was used to work through an example given in Astronomical Algorithms, while the Working Code (testing) 
cell was used to test and debug versions of the script prior to completion. 
