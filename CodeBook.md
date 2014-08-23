## Getting and Cleaning Data Project

Heather Wade

### Description
Additional information about the variables, data and transformations used in the course project for the Johns Hopkins Getting and Cleaning Data course.

### Source Data
A full description of the data used in this project can be found at [The UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

[The source data for this project can be found here.](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)

### Data Set Information
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 


### Attribute Information
For each record in the dataset it is provided: 
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration. 
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

### Section 1. Merge the training and the test sets to create one data set.
After setting the source directory for the files, read into tables the data located in
- features.txt
- activity_labels.txt
- subject_train.txt
- x_train.txt
- y_train.txt
- subject_test.txt
- x_test.txt
- y_test.txt

## Data sets

### Raw data set

In order to create a raw data set, the following regular expression was used:
`-(mean|std)[(]`. I.e. all variables containing `-mean(` or `-std(` in their
names were filtered.

Totally, the raw data set contains 68 variables:

 * `subject` - An identifier of the subject who carried out the experiment.
 * `label` - An activity label.

Plus 66 filtered features mined as described below.

The signals were used to estimate variables of the feature vector for each
pattern:  
`-XYZ` is used to denote 3-axial signals in the X, Y and Z directions.
 * `tBodyAcc-XYZ`
 * `tGravityAcc-XYZ`
 * `tBodyAccJerk-XYZ`
 * `tBodyGyro-XYZ`
 * `tBodyGyroJerk-XYZ`
 * `tBodyAccMag`
 * `tGravityAccMag`
 * `tBodyAccJerkMag`
 * `tBodyGyroMag`
 * `tBodyGyroJerkMag`
 * `fBodyAcc-XYZ`
 * `fBodyAccJerk-XYZ`
 * `fBodyGyro-XYZ`
 * `fBodyAccMag`
 * `fBodyAccJerkMag`
 * `fBodyGyroMag`
 * `fBodyGyroJerkMag`

The set of variables that were estimated from these signals are: 
 * `mean()`: Mean value
 * `std()`: Standard deviation

### Tidy data set

Tidy data set contains the same variables as the raw does, but the variables
were renamed according to following rules:
 * `All lower case when possible` - the variables names **were not** converted
   to lower case, since it would make them unreadable.
   Instead, the variable names were converted to satisfy `camlCase` rule.
 * `Descriptive (Diagnosis versus Dx)` - the variable names are descriptive,
   so nothing special should be done.
 * `Not duplicated` - the variable names are unique, so again nothing special
   had to be done.
 * `Not have underscores or dots or white spaces` - dashes and parentheses
   were removed from variable names.

To satisfy the requirements above, the following replacements were performed:
 1. Replace `-mean` with `Mean`
 1. Replace `-std` with `Std`
 1. Remove characters `-()`
 1. Replace `BodyBody` with `Body`



## Section 2. Extract only the measurements on the mean and standard deviation for each measurement. 
Create a logcal vector that contains TRUE values for the ID, mean and stdev columns and FALSE values for the others.
Subset this data to keep only the necessary columns.

## Section 3. Use descriptive activity names to name the activities in the data set
Merge data subset with the activityType table to cinlude the descriptive activity names

## Section 4. Appropriately label the data set with descriptive activity names.
Use gsub function for pattern replacement to clean up the data labels.

## Section 5. Create a second, independent tidy data set with the average of each variable for each activity and each subject. 
Per the project instructions, we need to produce only a data set with the average of each veriable for each activity and subject
