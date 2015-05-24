#Course Project Code Book
Data source: 
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Original description: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

The R script (run_analysis.R) does the following actions to clean up the data:

* Merges the training and test sets to create one dataset:
··* train/X_train.txt with test/X_test.txt, the result is a 10299x561 dataframe, as in the original description ("Number of Instances: 10299" and "Number of Attributes: 561").
··* train/subject_train.txt with test/subject_test.txt, the result is a 10299x1 data frame with subject IDs.
··* train/y_train.txt with test/y_test.txt, the result is a 10299x1 dataframe with activity IDs.

* Reads features.txt and extracts only the measurements of the mean and standard deviation for each sample. 
The result is a 10299x66 dataframe, because only 66 out of 561 attributes are measurements on the mean and standard deviation. 
All measurements are floating point numbers within the range [-1, 1].

* Reads activity_labels.txt Uses descriptive activity names to name the activities in the data set:

```
walking

walkingupstairs

walkingdownstairs

sitting

standing

laying
```

* The script also labels the data set with descriptive names: all feature names (attributes) and activity names are put into
 lower case, underscores and brackets are removed. Afterwards it merges the 10299x66 dataframe containing features with the 10299x1
 dataframes containing activity labels and subject IDs. The result is saved in a file called merged_clean_data.txt, a 10299x68 dataframe such that the
 first column contains subject IDs, the second column activity names, and the last 66 columns are measurements. Subject IDs are integers 
 in the range [1, 30]. The names of the attributes are the following:

```
tbodyacc-mean-x 

tbodyacc-mean-y 

tbodyacc-mean-z 

tbodyacc-std-x 

tbodyacc-std-y 

tbodyacc-std-z 

tgravityacc-mean-x 

tgravityacc-mean-y
```

* Finally, the script writes an independent tidy dataset with the average measurement for each activity and each subject in a file called
 dataset_averages.txt, a 180x68 dataframe, where the first column contains subject IDs, 
 the second is activity names, and then the averages for each of the 66 attributes are in columns 3-68.
 There are 30 subjects and 6 activities (180 rows set with averages).