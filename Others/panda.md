

## **Creating DataFrame**
- DataFrame
- Series

## **Summary Functions**

- df.points.describe()
- df.points.mean()
- df.taster_name.unique()
- df.taster_name.value_counts()


## **Slicing**


### Simple Look
- df.shape
- df.head()
- df.dtypes
- df.price.dtype

### (column)Index based

- df.iloc[0] # first row
- df.iloc[:, 7] # all rows only with 6th column
- df.iloc[:3, :] # first three rows
- df.iloc[[0, 1, 2, 3], :]  # first four rows
- df.iloc[-5:] # last five rows



### (column)Label based

- df.loc[0, 'country']
- df.loc[;,  ['taster_name', 'taster_twitter_handle', 'points']] # all rows with those specific columns


### Conditional Slicing

- df.country == "Italy" # Return a series where each value is True/False
- df.loc[df.country == "Italy"] # Returns every rows where country column value is 'Italy'
- df.loc[(reviews.country == 'Italy') & (reviews.points >= 90)] # returns every ros where country is Italy and points is higer than 90
- `df.loc[df.country.isin(['Italy', 'France'])] # Returs every row if country is Italy or France`
- `df.loc[df.price.notnull()] # returns every rows where price is not null.`


Here things in df.loc is Series, where each element is True/False and length is same as length of df.


- df.rename_axis("wines", axis='rows').rename_axis("fields", axis='columns') # it's renaming the index to wines and column to fields.





### Groupig

- df.groupby(points).price.mean
```
points
80     397
81     692
      ...
99      33
100     19
Name: points, Length: 21, dtype: int64
```

Here df.groupby(points) returns groups which are subset of the df. The each subset of df have same points. So here ur getting meann of price for each group. When the group is formed by the points value.


- `df.groupby('winery').apply(lambda df: df.title.iloc[0]) # create subsets of df based on winery, then for each subset of df only get first title`


- df.groupby(['country', 'province']).apply(lambda df: df.loc[df.points.idxmax()])

- df.groupby(['country']).price.agg([len, min, max])




## **Mainpulting Data**


### Simple

- df.set_index("title") # set the title column as index column
- df["critic"] = "everyone" # make all values in 'critic' column to "everyone"
- df["index_backward"] = range(len(df), 0, -1) # this will create a new column called 'index_backward' if it didn't existed
- df.points = df.points.astype('float64')
- df.rename(columns={'points':'score'}) # rename columns
- df.rename(index={0: 'firstEntry', 1: 'secondEntry'}) # rename index. But you rarely use this, if u want to rename index, use set_index()


### Map
Option1
```
review_points_mean = df.points.mean()
df.points.map(lambda p: p - review_points_mean)
```

Option2
```
def remean_points(row):
  row.points = row.points - review_point_mean
  return row

reviews.apply(remean_points, axis='column)

```

### Sorting
```
# sort df by certain column 'quality_score'
df.sort_values(by='quality_score') # ascending=True
df.sort_values(by='quality_score', ascending=False) # ascending=False
```

```
# sort by index
df.sort_index()
```

```
# sort by more tha one column at a time
df.sort_values(by=['country', 'len'])
```


### Combining

- pd. concat([canada_df, india_df]) # combine two dataframes where each have same columns

```
# .join() us used when both DataFrames have an index in common.

left = canadian_youtube.set_index(['title', 'trending_date'])
right = british_youtube.set_index(['title', 'trending_date'])

left.join(right, lsuffix='_CAN', rsuffix='_UK')

# here adding suffix is to prevent issue happening from both having same column name.

```
