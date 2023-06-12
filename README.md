# **Snow-Spotter-Data-Cleaning**
Create a cleaned dataset from Zooniverse workflow classification exports
## Summary
Zooniverse workflow classification exports provide a massive csv file with a huge range of data. However, for data analysis purposes, we are only interested in a a few fields. This scripts in this repository describe the code used to create a cleaned netCDF or csv file for Niwot Ridge water years 2016-2023. The final cleaned file will have columns for datetime, median value, mean value, and mean threshold value. This README will outline the general process of cleaning the data, but code for specific water years can be found within the jupyter notebook files. 

### **Downloading the workflow classifications export**

For downloading data from a specific workflow, it is easiest to use the [Panoptes command line interface](https://github.com/zooniverse/panoptes-cli). 
 
After downloading the required packages, run the following code in the command interface:
```python
panoptes workflow download-classifications --generate workflow.id filename.csv
```
“workflow.id” should be replaced with the unique numerical ID for a given workflow found on the workflow page of the Zooniverse website and “filename.csv” should be replaced with the preferred data export filename. 

### Cleaning the Data
Below is a brief summary of the process to clean the dataset. More detailed explanations and specific code can be found in the Jupyter Notebook files within this repository. 

1) Import packages
2) Open the annotations and subject_data columns from the classifications export in pandas
3) Create a function to the datetime from the subject_data column
4) Create a function to extract participant repsonse as a binary 1/0/Nan value from the annotations column
5) Use these two functions to create a new dataframe with columns for datetime and participant response
6) Calculate the median and mean participant response for each datetime
7) Create a final dataframe with columns for datetime, median value, and mean value
8) Add an additional column onto the dataframe for threshold mean, which
9) Save the dataframe as a netCDF or csv file
