# Getting and cleaning US wage data
---
Getting clean wage data from the Bureau of Labor Statistics is a difficult task and requires 
a lot of digging before the user get what they need. Below we have worked to simplify that 
process, removing some of the processing barriers and giving the user some general knowledge 
about the data sets so they get hit the ground running in their analyses.<br>
<br>
A comprehensive analysis of wage data is done annually by the Bureau of Labor Statistics 
(BLS). According to the [US Census Bureau,](https://www2.census.gov/geo/pdfs/reference/GARM/Ch13GARM.pdf) 
<i>"Counties containing the principal concentration of population—the largest city and 
surrounding densely settled area—are components of the MSA."</i> The inflections in wages 
in these regions are an important statistics used by the Office of Management and Budget and 
the US Census Bureau. Many mainstream jobs, such as those in finance and tech, are heavily 
researched throughout the country however, there are industries that are not as well defined 
such as agriculture and manufacturing.<br>
<br>
Data will be pulled from the [Bureau of Labor Statistics (BLS)](https://www.bls.gov/), 
a site managed by US Department of Labor that publishes research and datasets of for the 
general public to consume. This project will specifically use the [Quarterly Concensus of Employment and Wages (QCEW)](https://www.bls.gov/cew/) 
which houses variables such as job categories, wages, and job type densities. There are 
other datasets that would be important to include such as the [Annual reports](https://www.bls.gov/cew/cewbultncur.htm), 
[monthly unemployment publications](https://www.bls.gov/lau/), 
and [employment forecasts](https://www.onetonline.org/find/bright) but, we will focus on 
the wage statistics of counties and MSAs.

## Packages
---
- [glob](https://docs.python.org/2/library/glob.html) is used to group together file that we can work with in a dataframe
- [os](https://docs.python.org/2/library/os.html) will be used to navigate our file paths and modify files
- [pandas](https://pandas.pydata.org/) helps manage data and manipulate our sets for processing
- [urlretrieve](https://docs.python.org/3.4/library/urllib.request.html#legacy-interface) from [urllib](https://docs.python.org/2/library/urllib.html) allows us to access and scrape sites for specific URLs
- [time](https://docs.python.org/2/library/time.html) from [time](https://docs.python.org/2/library/time.html#time.time) is used to clock our code and identify bottlenecks
- [datetime](https://docs.python.org/2/library/datetime.html#datetime.datetime) from [datetime](https://docs.python.org/2/library/datetime.html) makes working with dates easier
- [zipfile](https://docs.python.org/2/library/zipfile.html) helps us extract the files fetched from [urlretrieve](https://docs.python.org/3.4/library/urllib.request.html#legacy-interface)
- [shutil](https://docs.python.org/2/library/shutil.html) from [rmtree](https://docs.python.org/2/library/shutil.html) quickly removes all files in a folder

## How to get started
---
Everything is written in Python 3 with Jupyter Notebook. Users can easily install both of these with 
[Anaconda](https://anaconda.org/anaconda/python). When the code is ran, files are downloaded in a `.csv` format
and stored in `/data`, so be sure to choose a repository that can store you data and be accessed later. The default
code gets data from 2005 through 2016 and each year is about 4 Gb of data with ~4,200 csv files. 