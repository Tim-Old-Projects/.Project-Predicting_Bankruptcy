###############################################################################
#    Date : 11/18/2018                                                        #
#    Author: Tamanna Baig                                                     #
#    Purpose: Exploratory Data Analysis                                       #
###############################################################################
#To clear the environment
rm(list = ls())

#Libraries used in the file

library(summarytools)
library(mlbench)
library(caret)
library(mice)
library(VIM)
library(DMwR)

#Loading the Dataset

dataset <- read.csv('data/Bankruptcy Master Dataset.csv', header = TRUE, sep=",", na.strings = "?")

#calculate correlation matrix
correlationMatrix <- cor(dataset, use = 'complete.obs')
print(correlationMatrix)
highlycorrelated <- findCorrelation(correlationMatrix, cutoff = 0.5)
length(highlycorrelated)
#Dropping the Highly correlated variables
new_dataset <- dataset[-c(highlycorrelated)]

#Imputing the Missing Values using MICE method
missing_ds <- subset(new_dataset, select = -c(class))
summary(missing_ds)

#Tabular view of missing values with respect to the columns they are present in
md.pattern(missing_ds)

#Visualizing missing values
mice_plot <- aggr(missing_ds, col=c('green','yellow'),
                    numbers=TRUE, sortVars=TRUE,
                    labels=names(missing_ds), cex.axis=.7,
                    gap=3, ylab=c("Missing data","Pattern"))

#Imputing the missing values
mice_impute <- mice(data = new_dataset, m = 5, method = 'pmm', seed = 500)

#Above Imputer method gives 5 datasets. Choose 1 using 'Complete' function
imputed_dataset <- complete(mice_impute, 1)
view(dfSummary(imputed_dataset))
