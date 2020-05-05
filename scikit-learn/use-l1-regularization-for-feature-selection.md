# use L1 regularization for feature selection

Univariate methods consider only one feature at a time when making a selection decision. Instead, we can make our selection using all of the features by including them in a linear model with L1 regularization. This type of regularization (sometimes called Lasso) penalizes the absolute magnitude of the coefficients, as compared to L2 (Ridge) regression which penalizes the square of the coefficients.

As the strength of regularization is increased, features which are less important for predicting the target are set to 0. This allows us to perform feature selection by adjusting the regularization parameter. We choose the parameter by finding the best performance on a hold-out set, or decide ahead of time how many features to keep.

For regression problems you can use sklearn.linear_model.Lasso, or sklearn.linear_model.LogisticRegression for classification. These can be used along with sklearn.feature_selection.SelectFromModel to select the non-zero coefficients. Otherwise, the code is similar to the univariate tests.

```python
from sklearn.linear_model import LogisticRegression
from sklearn.feature_selection import SelectFromModel

def select_features_l1(X, y):
    """ Return selected features using logistic regression with an L1 penalty """
    logistic = LogisticRegression(C=0.1, penalty="l1", random_state=7).fit(X, y)
    model = SelectFromModel(logistic, prefit=True)
    X_new = model.transform(X)
    selected_features = pd.DataFrame(model.inverse_transform(X_new), 
                                 index=X.index,
                                 columns=X.columns)
    selected_columns = selected_features.columns[selected_features.var() != 0]
    return selected_columns
```
