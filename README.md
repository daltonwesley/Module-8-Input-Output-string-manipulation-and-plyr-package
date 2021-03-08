# Module-8-Input-Output-string-manipulation-and-plyr-package

#First you needed to instal the  plyr package from the plyr library
install.packages("plyr")
library(plyr)

# Upload the dataset of the CSV file 
students <- read.table(file.choose(),header=T,sep=",")

#Make a new list by which sex and Grade means per gender are separted 
students_gendered_mean <- ddply(students, "Sex", transform, average_grade=mean(Grade))

#Create a new file
write.table(students_gendered_mean, "Students_Gendered_Mean")

#This command allows me to filter out names with the let "I,i" in it 
i_students <- subset(students, grepl("i", students$Name, ignore.case=T))

#Filtered data set for CSV file
write.table(i_students, "DataSet_Subset.csv", sep=",")

#Lastly visualize the data
students_gendered_mean
