# getting-and-cleaning-data
Getting and Cleaning Data Course Project
Tasks that script perform: Begining:

downloads and unpack data for the project
load necessary libraries
1.Merges the training and the test sets to create one data set. It is achived by steps:

creates a variable that contains names for dataset column
load test and train data (both X and y)
bind train and test data by rows
bind x and y data by columns
Extracts only the measurements on the mean and standard deviation for each measurement. In features_info.txt file we can inforamtion that labels that describe desirable variables contains in it's names mean() or std(), by using grepl we can select all labels that contains those phrases. Using vector of TRUE and FALSE (std_and_mean_variables) we can choose only mean and standard deviation columns or each measurement from data_binded.

Uses descriptive activity names to name the activities in the data set In activity_labels.txt thhere is an expleantion how numbers 1-6 represents activities. nr - stands for - activity 1 - WALKING 2 - WALKING_UPSTAIRS 3 - WALKING_DOWNSTAIRS 4 - SITTING 5 - STANDING 6 - LAYING

By using if loop script subsides values with their descriptive counterpart.

Appropriately labels the data set with descriptive variable names. By using gsub we can replace abbreviations by the more descriptive labels. By building a new labels we can use informations from features_info.txt file: Acc -> Accelerometer t -> time signal Gyro -> Gyroscope Jerk -> Jerk Signal f -> frequency Using cominations of this abbreviations we can encode labels and give them more descriptive names.

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

To perform group_by and summarise actions first we must test if measured variables are numerical and cathegorical variables are characters. If not, transorm them.

By performing this operation: data_task5_summarised <-data_task5 %>% group_by(subjects, Activities) %>% summarise_each(funs(mean))

Data is grouped and then mean function is applied to each variable
