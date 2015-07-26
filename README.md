# Getting-and-cleaning-data-project-assignment
Project assignment in the Coursera 'Getting and Cleaning Data' are presented in this repository.
Following are the steps needed to follow to work out project assignment
1. Download the data from the link link provided: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 
2. Understand about this data from the information line: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 
3. Load data into R console or R studio in order to clean the scattered data: i.  Give handy names to the variables :- shown in line 11-16.
 ii.  Merge X with X and Y with Y data sets from booth the 'test' and 'train' folders.lines 20-21
iii.Now get only columns having mean and standard deviations as features usign the function 'grep'
iv. Subset the the desired columns
v. correct column names. Line 33,40
vi. Next load and name activities in the activities data set usign descriptive activity names. line 35
vii.Then update values values on the activity data with correct names. Line 37
viii.Now bind all data into a single set. line 41
ix. get column means of all activity columns using  function colMeans. Line 46
x. Make a table of data containing column means. Line 48
