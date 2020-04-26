# Drop columns w categorical data

```python
# Get list of categorical variables
s = (X_train.dtypes == 'object')
object_cols = list(s[s].index)

drop_X_train = X_train.select_dtypes(exclude=['object'])
drop_X_valid = X_valid.select_dtypes(exclude=['object'])
```
