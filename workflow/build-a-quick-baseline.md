# build a quick baseline

```python
from sklearn.ensemble import RandomForestClassifier

# create a copy to work w
X = train.copy()

# save and drop lables
y = train.y
X = X.drop('y', axis=1)

# fill NANs
X = X.fillna(-999)

# Label encoder
for c in train.columns[train.dtypes == 'object']:
  X[c] = X[c].factorize()[0]
  
rf = RandomForestClassifier()
rf.fit(X, y)
```

# Plot 
```python
plt.plot(rf.feature_importances_)
plt.xticks(np.arrange(X.shape[1]), X.columns.tolist().rotation=90):
```
if you find data that has a particularly high or low value, then you could investigate further by looking up the mean and std. For the sake of simplicity, let's call that data x8.

```python
print( 'Mean', train.x8.mean())
print( 'std', train.x8, std())
train.x8.value_counts().head(15)
```
