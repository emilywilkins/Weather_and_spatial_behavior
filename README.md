# Weather_and_spatial_behavior
### Code associated with the paper titled "Social media reveal ecoregional variation in how weather influences visitor behavior in U.S. National Park Service units"(currently in review)

This repository contains many different .Rmd files used for data collection, cleaning, and analysis. It also contains some .csv files used as inputs for the R code.

### Steps to run code for data collection and processing:
Note: You should clear the R global environment after each step if your computer memory is 16 GB or less. Since this is a large dataset, I've included times it took things to run. Code was run on a Mac with 16 GB memory and 2.7 GHz Intel Core i5 processor. 

1.	Run python script: flickr_download_all_parks.py. Note, this is likely to take a few days.
2.	Run R script: data_cleaning.Rmd. Takes about 3 hours.
3.	Run R script: adding_weather_data.Rmd. Takes 1-2 days.
4.	Run R script: adding_elevation_data.Rmd. Takes about 2 weeks on one computer. 
5.	Run R script: Comparing_sample_sizes.Rmd. This is just a check to make sure all the data downloading up to this point has been correct. Samples sizes for each file should remain the same from step 2 through now. This will export a CSV file with any errors.
6.	Run R script: adding_osm_data.Rmd. This will take weeks on one computer (I split it between 5 computers and it still took 3-4 weeks). You will need at least 16 GB RAM to run this. 
7.	Run R script: PUDs_script.Rmd. This will first add distance to dirt roads as an additional column for each CSV (this will take 1-2 weeks on one computer). It will then filter the dataset to not include any photos by the same user on the same day within 10 meters of each other. Photos more than 10 meters apart by the same user are retained.
8.	Run R script: adding_weather_data_VC.RMD. This adds weather data for each point at the visitor center of each unit the photo was taken in.

### Steps to run code for analysis (done after all the above code is run to collect & clean data):

1.	Run R script: Visitation_Correlations.Rmd. This will get the correlations between Flickr PUD and NPS data
2.	Run R script: EDA.Rmd. This will generate a lot of info about all the variables. Correlations by ecoregion, boxplots for distributions, QQplots, etc. 
3.	Run R script: adding_categorical_variables.Rmd. This will add new columns to make all of the continuous independent variables either binary or categorical. 
4.	Run R script: ANOVAs.Rmd. This will run ANOVAs and t-tests on all the data by ecoregion and export to a csv with means by group, p-values, post-hoc, effect sizes etc. 
5.	Run R script: maps_by_temp.Rmd. This will make figures by park that show the spatial distribuions on hot vs cold days (e.g., figure 4 in the paper)
    
*** Note: you will have to change all the file paths to your own prior to running this analysis. Because I was working off a shared drive, I tended to include the full file path rather than just setting the working directory, just to be extra safe I wasn’t messing with other peoples’ files. I am aware this is not standard coding practice, but find it most cautious when working on a shared drive.
