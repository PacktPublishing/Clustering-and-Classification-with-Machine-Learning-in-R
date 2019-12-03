##################################################################
################ Expectation Max (EM) algorithm

# It follows an iterative approach, sub-optimal, which tries to find 
#the parameters of the probability distribution that has the 
#maximum likelihood of its attributes

#For each iteration, first is executed the E-Step (E-xpectation), 
#that estimates the probability of each point belongs to each cluster,
#followed by the M-step (M-aximization), 
#that re-estimate the parameter vector of the probability distribution of each class. 

##initialized by hierarchical model-based clustering. 
##Each cluster k is centered at the mean
#increased density for points near the mean


library(mclust)
require(fclust)

data(unemployment)
head(unemployment)

x=scale(unemployment) #to avoid bias

mc <- Mclust(x)            # Model-based-clustering
summary(mc)  


mc$modelName                # Optimal selected model ==> "VVV"
mc$G                        # Optimal number of cluster => 3
head(mc$z)              # Probality to belong to a given cluster
head(mc$classification) # Cluster assignement of each observation

library(factoextra)
# BIC values used for choosing the number of clusters
fviz_mclust(mc, "BIC", palette = "jco")
# Classification: plot showing the clustering
fviz_mclust(mc, "classification", geom = "point", 
            pointsize = 1.5, palette = "jco")
# Classification uncertainty
fviz_mclust(mc, "uncertainty", palette = "jco")

