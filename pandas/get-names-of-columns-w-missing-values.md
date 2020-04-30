# Get columns w missing values

```python
ols_with_missing = [col for col in X_train.columns
                     if X_train[col].isnull().any()]
```
