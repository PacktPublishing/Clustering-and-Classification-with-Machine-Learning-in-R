######################################################################
#####################################################################
######## Heirarchial Clustering R

library(fclust)
library(cluster)

head(unemployment)

df = scale(unemployment)
head(df)

#Agglomerative Hierarchical Clustering

# Dissimilarity matrix
d = dist(df, method = "euclidean")

library(cluster)
# Hierarchical clustering using Complete Linkage
hc1 = hclust(d, method = "complete" )

# Plot the obtained dendrogram
plot(hc1, cex = 0.6, hang = -1)

# Compute with agnes
hc2 = agnes(df, method = "complete")

# Agglomerative coefficient- strength of clustering
hc2$ac

hc3 = agnes(df, method = "ward")
pltree(hc3, cex = 0.6, hang = -1, main = "Dendrogram of agnes") 

## Divisive HC

# compute divisive hierarchical clustering
hc4 = diana(df)

# Divise coefficient; amount of clustering structure found
hc4$dc


# plot dendrogram
pltree(hc4, cex = 0.6, hang = -1, main = "Dendrogram of diana")

## identify sub-groups

# Ward's method
hc5 <- hclust(d, method = "ward.D2" )

# Cut tree into 4 groups
sub_grp <- cutree(hc5, k = 4) #work with 4 clusters

# Number of members in each cluster
table(sub_grp)
## sub_grp

library(tidyverse)
unemployment %>%mutate(cluster = sub_grp) %>%head

plot(hc5, cex = 0.6)
rect.hclust(hc5, k = 4, border = 2:5)

library(factoextra)
fviz_cluster(list(data = df, cluster = sub_grp))

## determine the optimal cluster number

fviz_nbclust(df, FUN = hcut, method = "silhouette")

fviz_nbclust(df, FUN = hcut, method = "wss")
