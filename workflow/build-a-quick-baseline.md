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
