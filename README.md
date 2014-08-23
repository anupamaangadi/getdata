# Getting and Cleaning Data Project

This repo contains project code for `Getting and Cleaning Data` course given
by John Hopkins university on Coursera.

## Script

The script contains a function `run.analysis()` that performs the
actual job:
 * reads the train and the test data sets and merges them
 * processes the merged data set (extract the relevant variables,
   adds descriptive activity names, etc.)
 * writes the merged data set to `rawdata.csv`
 * generates the tidy data set
 * writes the tidy data set to `tidydata.csv`
 * returns the tidy data set

