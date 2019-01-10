##############################################################################
#    Date : 12/05/2018                                                        #
#    Author: Tamanna Baig                                                     #
#    Purpose: Random Forest                                                   #
#    Continued From: Exploratory Data Analysis                                #
###############################################################################

# Random Forest Regression

library(caTools)

# Encoding the target feature as factor
imputed_dataset$class <- as.factor(imputed_dataset$class)

# Splitting the imputed dataset into the Training set and Test set
# install.packages('caTools')
library(caTools)
set.seed(123)
split = sample.split(imputed_dataset$class, SplitRatio = 0.7)
training_set = subset(imputed_dataset, split == TRUE)
test_set = subset(imputed_dataset, split == FALSE)

# Feature Scaling
training_set[-c(1,2,26)] = scale(training_set[-c(1,2,26)])
test_set[-c(1,2,26)] = scale(test_set[-c(1,2,26)])

#To call Random Forest classifier
library(randomForest)
forest = randomForest(x = training_set[-c(26)],
                      y = training_set$class,
                      ntree = 25)

#Plotting the RF classifier
plot(forest)

#Predicting the classifier
y_pred = predict(forest, newdata = test_set[-26])
y_pred

#Confusion Matrix
cm = table(test_set[,26], y_pred != 0)
cm

#The Accuracy of the classifier
accuracy <- (cm[1,1] + cm[2,2])/(cm[1,1] + cm[2,2]+ cm[1,2]+ cm[2,1])
accuracy
#The precision of the classifier (how often it is correct)
precision_cm <- (cm[2,2])/(cm[2,2]+cm[1,2])
precision_cm
#Recall/sensitivity/True positive rate
recall_cm <- cm[2,2]/(cm[2,2]+cm[2,1])
recall_cm
####################################################################################################
##Show Time Series Effect
####################################################################################################

training_set2 <- imputed_dataset[1:35000,]
test_set2 <- imputed_dataset[35001:43405,]

#################################################################
#To call Random Forest classifier on Model2
library(randomForest)
forest2 = randomForest(x = training_set[-c(26)],
                      y = training_set$class,
                      ntree = 25)

#Plotting the RF classifier for Model2
plot(forest2)

#Predicting the classifier for Model2
y_pred2 = predict(forest2, newdata = test_set2[-26])
y_pred2

#Confusion Matrix for Model2
cm2 = table(test_set2[,26], y_pred2 != 0)
cm2

#The Accuracy of the classifier for Model2
accuracy2 <- (cm2[1,1] + cm2[2,2])/(cm2[1,1] + cm2[2,2]+ cm2[1,2]+ cm2[2,1])
accuracy2
#The precision of the classifier for Model 2 (how often it is correct)
precision_cm2 <- (cm2[2,2])/(cm2[2,2]+cm2[1,2])
precision_cm2
#Recall/sensitivity/True positive rate For Model2
recall_cm2 <- cm2[2,2]/(cm2[2,2]+cm2[2,1])
recall_cm2
