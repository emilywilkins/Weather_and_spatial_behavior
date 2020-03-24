# Weather_and_spatial_behavior
Code associated with the paper titled "How weather affects visitor behavior within U.S. national parks"

(paper currently in prep, to be submitted shortly)

This repository contains many different .Rmd files used for data collection, cleaning, and analysis. It also contains some .csv files used as inputs for the R code.

## Steps to run code for data collection and processing:

1.	Run python script: flickr_download_all_parks.py
    a.	Note, this is likely to take a few days
2.	Run R script: data_cleaning.Rmd
    a.	Takes about 3 hours
    b.	Clear R global environment before going to the next step
3.	Run R script: adding_weather_data.Rmd
    a.	Takes 1-2 days
    b.	Clear R global environment before going to the next step
4.	Run R script: adding_elevation_data.Rmd
    a.	Takes about 2 weeks on one computer (I split it between multiple computers)
    b.	Clear R global environment before going to the next step
5.	Run R script: Comparing_sample_sizes.Rmd
    a.	This is just a check to make sure all the data downloading up to this point has been correct. Samples sizes for each file should remain the same from step 2 through now. This will export a CSV file with any errors.
6.	Run R script: adding_osm_data.Rmd
    a.	This will take weeks on one computer (I split it between 5 computers and it still took 3-4 weeks). You will need at least 16 GB RAM to run this. 
    b.	Clear R global environment before going to the next step
7.	Run R script: PUDs_script.Rmd
    a.	This will first add distance to dirt roads as an additional column for each CSV (this will take 1-2 weeks on one computer)
    b.	It will then filter the dataset to not include any photos by the same user on the same day within 10 meters of each other. Photos more than 10 meters apart by the same user are retained.
    c.	Clear R global environment before going to the next step
8.	Run R script: adding_weather_data_VC.RMD
    a.	This adds weather data for each point – both Flickr and control – at the visitor center of each unit the photo was taken in.

## Steps to run code for analysis (done after all the above code is run to collect & clean data):

1.	Run R script: Visitation_Correlations.Rmd
    a.	This will get the correlations between Flickr PUD and NPS data
2.	Run R script: EDA.Rmd
    a.	This will generate a lot of info about all the variables. Correlations by ecoregion, boxplots for distributions, QQplots, etc. 
3.	Run R script: adding_categorical_variables.Rmd
    a.	This will add new columns to make all of the continuous independent variables either binary or categorical. 
4.	Run R script: ANOVAs.Rmd
    a.	This will run ANOVAs and t-tests on all the data by ecoregion and export to a csv with means by group, p-values, post-hoc, effect sizes etc. 
5.	Run R script: maps_by_temp.Rmd
    a.	This will make figures by park that show the spatial distribuions on hot vs cold days (e.g., figure 4 in the paper)
    
*** Note: you will have to change all the file paths to your own prior to running this analysis. Because I was working off a shared drive, I tended to include the full file path rather than just setting the working directory, just to be extra safe I wasn’t messing with other peoples’ files. I am aware this is not standard coding practice, but find it most cautious when working on a shared drive.
