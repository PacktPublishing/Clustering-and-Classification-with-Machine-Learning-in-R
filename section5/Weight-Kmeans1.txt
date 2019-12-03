#################################################################
############ Weighted K-Means Clustering

#entopy weighted k-means clustering algorithm is a subspace clusterer 
#ideal for high dimensional data
#each cluster we also obtain variable weights that provide a relative 
#measure of the importance of each variable to that cluster

library(wskm)
require(fclust)

data(unemployment)
head(unemployment)

x=scale(unemployment) #to avoid bias

## weighted k means

myewkm = ewkm(x, 3, lambda=1, maxiter=100)
#lambda should be 1-3

plot(x, col=myewkm$cluster)

plot(myewkm)

myewkm$cluster

myewkm$weights
