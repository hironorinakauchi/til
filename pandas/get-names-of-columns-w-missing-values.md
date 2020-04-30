# Get columns w missing values

```python
cols_with_missing = [col for col in X_train.columns
                     if X_train[col].isnull().any()]
```
