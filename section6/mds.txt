######## Multi Dimensional Scaling (MDS)

##Multidimensional scaling is a method that allows you to visualize 
##how near (pattern proximities) objects are to each other
## MDS can produce a representation of data with lower dimension space. 
#PCA can be regarded as the simplest form of MDS if the 
#distance measurement used in MDS equals the covariance of data.

head(swiss)

swiss.dist =dist(swiss)
swiss.mds = cmdscale(swiss.dist, k=2) #2 components

plot(swiss.mds[,1], swiss.mds[,2], type = "n", main = "cmdscale
(stats)")

text(swiss.mds[,1], swiss.mds[,2], rownames(swiss), cex = 0.9,
     xpd = TRUE)


library(MASS)

##non metric MDS

swiss.nmmds = isoMDS(swiss.dist, k=2)

plot(swiss.nmmds$points, type = "n", main = "isoMDS (MASS)")
text(swiss.nmmds$points, rownames(swiss), cex = 0.9, xpd = TRUE)

