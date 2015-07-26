I am have put command instructios as well. It looks similar to my .R file but servers purpose of codebook as well since I have put down all the instructions/comments along with the codes. 
1.Designate working directory to the one in which downloaded data was unzipped. In my pc it is,
setwd("~/DATA-SCIENCE/Course 3- Getting and cleaning data/data/getdata-projectfiles-UCI HAR Dataset/UCI HAR Dataset")
#Cleaning workspace:
rm(list=ls())
#Q.1 asks to merge the training and test data sets using R codes. I am doing it as follows
# first read the data from files usign followign codes. Make sure you first look into the folder and data information to see the available data there 
#load dplyr and reshape2 libraries
library(dplyr)
library(reshape2)
#then read or import the X and Y test and train data and assign them handy names
 testX <- read.table("./test/X_test.txt") 
 testY <- read.table("./test/Y_test.txt")
 trainY <- read.table("./train/Y_train.txt")
 trainX <- read.table("./train/X_train.txt")
 subjectTrain = read.table("./train/subject_train.txt")
 subjectTest = read.table("./test/subject_test.txt")


# Next merge X and y data to crate a combined dataset
datasetX <- rbind(trainX,testX)
datasetY <- rbind(trainY,testY)
#Also create merge subject test and train data 
SubjectData <- rbind(subjectTrain,subjectTest)
# Also import features from the text files 
features <-  read.table("./features.txt")
# Now get only columns having mean and standard deviations as features
# I am usign the function 'grep': Usage grep(pattern, x) searches for a particular pattern in each element of a vector x
# more on grep at: http://rfunction.com/archives/1481 
mean_stdv_features <- grep("-(mean|std)\\(\\)", features[, 2])
#Now subset the desired columns;
datasetX <- datasetX[, mean_and_std_features]
#Not column names needs to be corrected;
names(datasetX)<- features[mean_stdv_features, 2]
# Next name activities in the activities data set usign descriptive activity names
activities <- read.table("activity_labels.txt")
#Then update values values on the activity data with correct names
datasetY[, 1] <- activities[datasetY[, 1], 2]
names(datasetY) <- "activity"
# also properly label the data set with descriptive variable names
names(subjectData) <- "subject"
# Now bind all data into a single set;
allData <- cbind(datasetX, datasetY, subjectData)
#You may also need the call the functon plyr as: 
require(plyr)
#Next create another tidy data set with mean of each variable:
AverageValues <- ddply(allData, .(subject, activity), function(x) colMeans(x[, 1:66])) 
# One can now get a table of average data of all variables:
write.table(AverageValues, "AverageValues.txt", row.name=FALSE)
# Thank you ! #





