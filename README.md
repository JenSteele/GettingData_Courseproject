# GettingData_Courseproject
Course Project 1 from Getting and Cleaning Data Course

This project is designed to follow the five steps outlined in the instructions:
1) Merges the training and the test sets to create one data set.
2) Extracts only the measurements on the mean and standard deviation for each measurement
3) Uses descriptive activity names to name the activities in the data set
4) Appropriately labels the dataset with descriptive variable names
5) Create a tidy data set

I'll outline my methods for each of the steps.

1) Merges the training and the test sets to create one data set.
  a) Load datasets into R (six datasets, 3 for train, 3 for test) and label columns
    Note:  In this step I've used getwd() to find the path to avoid displaying personal information, I realize this is     a fairly messy way of doing it (as the working directory would need to be set properly prior to running this          step).

  b) merge the datasets
    i) create one 'train' dataset by column binding across y_train.txt, subject_train.txt and X_train.txt
    ii) create one 'test' dataset by column binding across y_test.txt, subject_test.txt and X_test.txt)
    iii) create one overall dataset by row binding across the train and test datasets

2) Extracts only the measurements on the mean and standard deviation for each measurement
  Note:  I have included meanfreq even though it is a weighted average rather than a 'true' mean
  Here I first selected columns with 'mean' in their name, then columns with 'std' in their name, and created two       datasets, one with means and one with standard deviations.  I then combined these datasets with the observation       details (subject # and activity) to create one large dataset with mean and standard deviations

3) Uses descriptive activity names to name the activities in the data set
  I uploaded the activity labels and merged the activity descriptor with the messy data set by the activity number.

4) Appropriately labels the dataset with descriptive variable names
  This had mostle been done in step 1, when I included the column labels with each dataset.  At this point I just cleaned up the names a bit using the make.names command.  I did not want to make too many changes to the labels to avoid losing any necessary information.
  
5) Create a tidy data set
I chose to make a long tidy data set, wtih each row representing a unique subject/activity pair, and recorded the mean  for each subject/activity pair as a different observation.

Finally, in order to read the txt file into R the following command can be used:
  url <- "http://s3.amazonaws.com/coursera-uploads/user-6ee89d8bc9a34db64ddd8047/975114/asst-3/5d8f06d033e511e58c715bb         63fb305dd.txt"
  test <- read.table(url,header=TRUE)
It will create a local dataframe named test
