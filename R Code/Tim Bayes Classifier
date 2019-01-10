##############################################################################
#    Date : 12/05/2018                                                       #
#    Author: Tim Mango                                                       #
#    Purpose: Predict Bankruptcy with Naive Bayes Classifier                 #
##############################################################################

##Libraries Used
#################################################################
library(e1071)
library(naivebayes)
library(mlbench)
library(caTools)

##Prepare Data
#################################################################
dataset <- read.csv(file="/Users/Mango/Downloads/Bankruptcy Master Dataset.csv", header = TRUE, sep=",", na.strings = "?")

working.data <- dataset[-c(1,2,67)]

testing.data<- working.data

Bankruptcy <- as.factor(dataset$Class)

ModelData1 <- cbind(Bankruptcy,working.data)

ModelData <- ModelData1[-c(5,6,9,13,15,17,21,24,27,29,37,39,40,41,44,47,52,55,57,58,60,61,64)]
##################################################################
# Splitting the dataset into the Training set and Test set
set.seed(123)
split = sample.split(ModelData, SplitRatio = 0.7)
train_data = subset(ModelData, split == TRUE)
test_data = subset(ModelData, split == FALSE)

##################################################################
Model1 <- naiveBayes(Bankruptcy~., data=train_data)
pred1 <- predict(Model1, test_data)

table(pred1, test_data$Bankruptcy)

##Show Time Series Effect
#################################################################

train_data2 <- ModelData[1:35000,]
test_data2 <- ModelData[35001:43405,]
#################################################################
Model2 <- naiveBayes(Bankruptcy~., data=train_data2)
pred2 <- predict(Model2, test_data2)

table(pred2, test_data2$Bankruptcy)
##################################################################
