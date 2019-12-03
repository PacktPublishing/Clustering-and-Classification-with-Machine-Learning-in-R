##############################################################
######### Feature selection: select the most important variables

setwd("F:\\DataMining_R\\3_LectureData\\dimReducn")

library(FSelector)

##Correlation filter
##weights of continous attributes basing on their correlation with continous class
##attribute

library(mlbench)
data(BostonHousing)

d=BostonHousing[-4] # only numeric variables
head(d)

weights = linear.correlation(medv~., d)
print(weights)
subset = cutoff.k(weights, 3)
f = as.simple.formula(subset, "medv")
print(f)

weights = rank.correlation(medv~., d)
print(weights)
subset = cutoff.k(weights, 3)
f = as.simple.formula(subset, "medv")
print(f)

############# Work with both Qualitative and Quantitative Predictors

mat=read.csv("student-mat.csv")

head(mat)

##G3 is the response variable-- final maths score of a class

## Quantiative predictors include: G1 & G2 (first and second term scores),age, study time
## Qualitative predictors include: sex,father's job, mum's job, internet


## select the most important variables in influencing G3

## CFS method
result =cfs(G3 ~ ., mat)
f = as.simple.formula(result, "G3")
print(f)

## Chi-squared method of variable selection

##chi-square test is a statistical test of independence
##calculate chi-square statistics between every feature variable and 
#the target variable

##observe the existence of a relationship between the variables 
#and the target
##target variable is independent of the feature variable, 
#we can discard that feature variable
weights = chi.squared(G3 ~ ., mat)
#weights of discrete attributes basing on a chi-squared test
print(weights)
subset = cutoff.k(weights, 5) #a cut-off above which we retain predictors
f = as.simple.formula(subset, "G3")
print(f)


## information gain method for variable selection
##which predictors provide the most information about the target variable of interest.

weights = information.gain(G3 ~ ., mat)
print(weights) #% information provided

subset = cutoff.k.percent(weights, 0.75)
f = as.simple.formula(subset, "G3")
print(f)

