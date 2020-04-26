# Build a random forest based model using OneHotEncoding 

```python
from sklearn.impute import SimpleImputer

# All categorical columns
object_cols = [col for col in X_train.columns if X_train[col].dtype == "object"]

# Columns that will be one-hot encoded
low_cardinality_cols = [col for col in object_cols if X_train[col].nunique() < 10]

# Fill in the lines below: imputation
my_imputer = SimpleImputer(strategy='most_frequent')
imputed_X_test = pd.DataFrame(my_imputer.fit_transform(X_test))

# Fill in the lines below: imputation removed column names; put them back
imputed_X_test.columns = X_test.columns 
imputed_X_test.index = X_test.index ###FIX

#### ONEHOT ENCODING FOR DATA #####
from sklearn.preprocessing import OneHotEncoder

# Apply one-hot encoder to each column with categorical data
OH_encoder = OneHotEncoder(handle_unknown='ignore', sparse=False)
OH_cols_train = pd.DataFrame(OH_encoder.fit_transform(X_train[low_cardinality_cols]))
OH_cols_valid = pd.DataFrame(OH_encoder.transform(X_valid[low_cardinality_cols]))
OH_cols_test = pd.DataFrame(OH_encoder.transform(imputed_X_test[low_cardinality_cols]))

# One-hot encoding removed index; put it back
OH_cols_train.index = X_train.index
OH_cols_valid.index = X_valid.index
OH_cols_test.index = imputed_X_test.index ####FIX

# Remove categorical columns (will replace with one-hot encoding)
num_X_train = X_train.drop(object_cols, axis=1)
num_X_valid = X_valid.drop(object_cols, axis=1)
num_X_test = imputed_X_test.drop(object_cols, axis=1) ####FIX

# Add one-hot encoded columns to numerical features
OH_X_train = pd.concat([num_X_train, OH_cols_train], axis=1)
OH_X_valid = pd.concat([num_X_valid, OH_cols_valid], axis=1)
OH_X_test = pd.concat([num_X_test, OH_cols_test], axis=1)

##### BUILD MODEL AND CREATE SUBMISSION ####
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error

# normalize datatypes columns
#for colName in  ['BsmtFinSF1', 'BsmtFinSF2', 'BsmtUnfSF', 'TotalBsmtSF', 'BsmtFullBath', 'BsmtHalfBath', 'GarageCars', 'GarageArea']:
#    OH_X_train[colName] = OH_X_train[colName].astype('float64')
#    OH_X_valid[colName] = OH_X_train[colName].astype('float64')

# Build model
model = RandomForestRegressor(n_estimators=100, random_state=0)
model.fit(OH_X_train, y_train)
preds_test = model.predict(OH_X_test)

# Save test predictions to file
output = pd.DataFrame({'Id': OH_X_test.index,
                       'SalePrice': preds_test})
output.to_csv('submission.csv', index=False)
```
