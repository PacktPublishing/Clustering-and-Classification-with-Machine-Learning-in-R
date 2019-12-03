#### Singular Value Decomposition (SVD)

#### matrix factorization (decomposition),
#### factorize matrices into two orthogonal matrices and diagonal matrices
#### SVD can reduce redundant data (linearly dependent)

head(swiss)
swiss = swiss[,-1] #remove categorical variable

swiss.svd = svd(swiss)

##plot the percentage of variance explained 
##cumulative variance explained

plot(swiss.svd$d^2/sum(swiss.svd$d^2), type="l", xlab=" Singular
vector", ylab = "Variance explained")

##cumulative variance explained by the components
plot(cumsum(swiss.svd$d^2/sum(swiss.svd$d^2)), type="l",
     xlab="Singular vector", ylab = "Cumulative percent of variance
explained")
