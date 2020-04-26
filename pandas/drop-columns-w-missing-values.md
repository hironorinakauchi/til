# Drop columns w missing values 

```python
# To keep things simple, we'll drop columns with missing values
cols_with_missing = [col for col in X.columns if X[col].isnull().any()] 
X.drop(cols_with_missing, axis=1, inplace=True)
X_test.drop(cols_with_missing, axis=1, inplace=True)
```

[source](https://www.kaggle.com/ironorih/exercise-categorical-variables/edit)
