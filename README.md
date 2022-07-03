# Principal-Component-Analysis

## Principal Component Analysis is used to perform dimensionality reduction on datasets, which is the idea of removing unnecessary portions and reducing computational costs. During PCA, the initial dataset goes through some sort of transformation from its original coordinate system to a new coordinate system, where the axis is determined by the two greatest variance directions of the inital datset.
![Screen Shot 2022-07-02 at 11 54 23 PM](https://user-images.githubusercontent.com/102645083/177028746-ab085192-5e64-4e57-9294-37f77cbea3d5.png)

## Our example is based on a dataset with 1,000 samples and two features. We start with finding the 2 x 2 covariance matrix, where the diagonal values are the variance of each feature, and the other two being the covariance of the two features. Because the covaraince is commutative (cov(f1,f2) = cov(f2,f1)), the covariance matrix is symmetric with resepect to the main diagonal, which means we can find the diagonal(D) and orthogonal(P) matrices.
<img width="344" alt="Screen Shot 2022-07-03 at 12 10 18 AM" src="https://user-images.githubusercontent.com/102645083/177029190-90942d6e-b857-4fab-a0ce-e3bf6efe9029.png">
