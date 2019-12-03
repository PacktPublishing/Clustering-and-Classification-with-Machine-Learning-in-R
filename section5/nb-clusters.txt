#####################################################################
#### Other ways of determining numbers of cluster

head(iris)
data=iris[,-c(5)] ##consider the numerical predictors only

library(NbClust)

par(mar = c(2,2,2,2))    #  Set margins as: c(bottom, left, top, right)

nb = NbClust(data, method = "kmeans")
## DECIDE on suitable cluster numbers
## check clusters from 2-15

# Histogram, breaks =15 as our algorithm checks from 2 to 15 clusters
hist(nb$Best.nc[1,], breaks = 15)
#2 as the best number of clusters 
