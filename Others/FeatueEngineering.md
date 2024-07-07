# Feature Engineering

# MI Score
Features: All features must be numerical. Therefore, you first need to convert any categorical features into numerical features.
Target: The target variable can be either categorical or continuous (regression).

Calculate MI score for all features then remove a few features with low MI score. You can use mutual_info_regression or mutual_info_classification depending on whether target is categorical or numerical.  Before applying these functions, you first need to convert categorical features into numerical features. That said every featrues dtype have to be either float or int. Btw it’s important to note that not all features with low MI score are useless.



## Mathematical transformation

Create new features:
df['stroke_ratio'] = df.stroke/df.bore
df['displacement'] = (np.pi * ((0.5 * df.bore) ** 2) * df.stroke * df.num_of_cylinders)

Change distribution of the data:
accidents["LogWindSpeed"] = accidents.WindSpeed.apply(np.log1p)

## Count

Coutning number of True:
boolean_features = ["Amenity", "Bump", "Crossing", "GiveWay”]
accidents["RoadwayFeatures"] = accidents[boolean_features].sum(axis=1)

Couting number of ingredients that was used
concrete["Components"] = concrete[components].gt(0).sum(axis=1)

## Building-Up and Breaking-Down Features (string features)

Building-Up
autos['make_and_style'] = autos['make'] + "_" + autos['body_style']

Breaking-Down:
customer[["Type", "Level"]] = customer['Policy'].str.split(" ", expand=True)


## Group TransFroms

Example1:
Here transform() gets mean of values in column for each sub DataFrames, and then putting those values bakc to all corressponding rows. So for exmaple, if there were 50 subgroups, it's getting 50 values. Then it put those values back to each all corresponding rows(13000 rows)

customer["AverageIncome"] = customer.groupby('State')['Income'].transform('mean')

Example2
customer['StateFreq'] = customer.groupby('State')['State'].transform('count')/customer.State.count()


## Clustering (K-Means Algorithm)
Features: All features must be numerical. Therefore, you first need to convert any categorical features into numerical features.
Target: There is no target, since this is unsupervised learning.

How K-Means Clustering Works

1. Define number of centroids
2. Randomly scatter those centroids

Repeat:
assign points to the closet centroids
recalculate the position of each centroid as mean of assigned points


from sklearn.cluster import KMeans

X = df.loc[:, ["MedInc", "Latitude", "Longitude”]]
kmeans = KMeans(n_clusters=6)
X[“Cluster"] = kmeans.fit_predict(X)
X[“Cluster"] = X["Cluster"].astype("category")


## PCA
Feautres: all features shoudl be numerical
Target: no need to think about it

What is PCA and how it works?
PCA is like creating N number of new feautues(PCA Components) using existing N features. 
These each components tell how much variance it has. btw before applying PCA u should standride features.

Create new features
Let’s say we have tow features and with this we created two components PC1 and PC2. Then calculate mI score for these and find out pc1 has a higher score than pc2.  then we can think of ceeating new feature which is product of feature1 and feature2. Otherwise ration of feature1 and feature2. 

Dimensionaly Reduction:
Drop some componenets with low variance.

## Target Encoding


