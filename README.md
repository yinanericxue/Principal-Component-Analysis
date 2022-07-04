# Principal Component Analysis

## PCA is used to perform dimensionality reduction on datasets, which is the idea of removing unnecessary features and reducing computational costs. During PCA, the initial dataset goes through some sort of transformation from its original coordinate system to a new coordinate system, where the axis is determined by the two greatest variance directions of the inital datset.
![Screen Shot 2022-07-02 at 11 54 23 PM](https://user-images.githubusercontent.com/102645083/177028746-ab085192-5e64-4e57-9294-37f77cbea3d5.png)

## Our example is based on a dataset with 1,000 samples and two features. We start with finding the 2 x 2 covariance matrix, where the diagonal values are the variance of each feature, and the other two being the covariance of the two features. Because the covariance is commutative (cov(f1,f2) = cov(f2,f1)), the covariance matrix is symmetric with resepect to the main diagonal, which means we can find the diagonal(D) and orthogonal(P) matrices.
![Screen Shot 2022-07-03 at 6 42 38 PM](https://user-images.githubusercontent.com/102645083/177067260-1e7379a9-f929-4563-ab2f-da58914c85c4.png)

## In matrix D, the diagonal values are the eigenvalues of the covariance matrix ordered from largest to smallest from left to right. Eigenvalues represent the total amount of variance that can be explained by a given principal component, and we order them based on their absolute values. On the other hand, matrix P includes all the corresponding eigenvectors to matrix D. While our example only has two features / eigenvalues, it's important to note that when there are many more, we typically only need a few of the largest eigenvalues to restore the majority of the covariance matrix.
![Screen Shot 2022-07-03 at 12 17 06 AM](https://user-images.githubusercontent.com/102645083/177029399-ba24c01e-94cd-49db-92a8-4b4ffe78eaf5.png)

## Now if we want to keep the more important feature out of the two, we transpose P and multiply its first row to the dataset. We now get
![Screen Shot 2022-07-03 at 7 34 26 PM](https://user-images.githubusercontent.com/102645083/177071617-60775841-26a9-4379-bc34-911df8e7b42c.png)

## However, what we really care about is whether we can restore the initial dataset using the features from this new dimension. In our code, we first used "pca.pca(data,1)" to have one feature in the new dimension. When we tried to recover the initial data, some of the original information were lost, but the general trend of the data is still there.
![Screen Shot 2022-07-03 at 6 58 27 PM](https://user-images.githubusercontent.com/102645083/177068550-152e89e6-d50e-4647-8306-752ece37f4c3.png)

## If we use "pca.pca(data,2)" and have two features in the new dimension. We will be able to restore the data back to its originality without any loss.
![Screen Shot 2022-07-03 at 7 15 45 PM](https://user-images.githubusercontent.com/102645083/177070017-58bf2ff2-7010-4eec-8852-4dac1e4d4055.png)

## The math behind this is quite simple. Because there are less values in Y comparing to X, some parts of matrix P never get used when recovering back to X. Specificaaly, when we only kept one of the two features in the example, the second column of P was never used because the second feature of Y is zero.
![Screen Shot 2022-07-03 at 7 33 53 PM](https://user-images.githubusercontent.com/102645083/177071568-c6b483a3-cf08-457f-b6f9-47be4f5b7332.png)
