##############################################################################
#    Date : 11/20/2018                                                       #
#    Author: Tim Mango                                                       #
#    Purpose: Explore Correlation of Variables                               #
##############################################################################

#Libraries Used
###################
library(ggcorrplot)
library(summarytools)

#Dataset and Model Data
##################
dataset <- read.csv(file="/Users/Mango/Downloads/Bankruptcy Master Dataset.csv", header = TRUE, sep=",", na.strings = "?")

working.data <- dataset[-c(1,2,67)]

#Summary Information for Dataset
##################
view(dfSummary(dataset))

#Defining Information for Correlation Matrix

corrdata <- cor(working.data, use = "complete.obs")
corr <- round(corrdata, 1)
p.mat <- cor_pmat(working.data)

#############################
##Note that the number of digits that corrdata is rounded to
##drastically changes the number of statistically correlated variables
##I made the choice of rounding to 1 digit
#############################

## Basic Correlation Plot to see the data
#############################
ggcorrplot(corr, method= "square", type = "lower", title = "Correlation of Response Variables",
  legend.title = "Correlation", show.diag = FALSE,
  lab = FALSE)

##Correlation plot with hierarchical clustering
####  x marks mean that there is statistically no correlation at p=0.05
ggcorrplot(corr, method= "square", type = "lower", title = "Correlation of Response Variables",
  legend.title = "Correlation", show.diag = FALSE, hc.order = TRUE, hc.method = "complete",
  p.mat = p.mat, sig.level = 0.05, insig = "pch",
  pch = 4, pch.col = "black", pch.cex = 3,lab = FALSE)
