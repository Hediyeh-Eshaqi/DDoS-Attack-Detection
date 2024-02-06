## DDoS-Attack-Detection

## Dataset
This dataset contains 7 files named LDAP, MSSQL, NetBIOS, Portmap, Syn, UDPLag, UDP with CSV extension. Also, this dataset contains 88 features.
[Dataset download link](https://drive.google.com/file/d/1v7ZeffblKhW_wYApmoxaTqHJvPDp2r-_/view?usp=share_link)

## Target
The dataset is divided into two categories for DDoS attack detection and classification. 'BENIGN' is labeled '0' and other attacks are labeled with '1' in the dataset created to identify the attack on network traffic.

## Data preprocess
I used some initial preprocess to the dataset as follows:
- removing rows with nan values
- removing rows with infinity values
- removing columns that only contain zeros
- adding 0 to 'BENIGN' labels and 1 to others to create the final labels
- applying min-max scale for normalization

after this preprocess the number of features reduced to 70 from 88

## Principal component analysis (PCA)
according to the large number of features, I used PCA to reduce the feature size as much as enough.


follwing graph is the "total explained variance" based on the "number of principal components"

![alt text](/images/pca.png)


Clearly, more principal components lead to more explained variance, but notice that adding an additional component from k = 30 to k > 30 does not provide much additional explained variance. Thus, it doesn’t make sense, based on this plot, to use k greater than 30.
so i decided to use k = 30;
## Model:
I used train_test_split from sklearn.model_selection to split my data into train and test. then i used SVC(Support vector classifier) from sklearn.svm as my prediction model.
## Results:
accuracy: 99.92610837438424%

true positive :  99.88270980788675%

true negative :  99.97082725567826%