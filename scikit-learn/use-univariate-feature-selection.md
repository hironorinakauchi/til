# Use Univariate Feature Selection
use SelectKBest with the f_classif scoring function to choose 40 features from the 91 features in the data. 
The simplest and fastest methods are based on univariate statistical tests. For each feature, measure how strongly the target depends on the feature using a statistical test like 𝜒2 or ANOVA.
From the scikit-learn feature selection module, feature_selection.SelectKBest returns the K best features given some scoring function. For our classification problem, the module provides three different scoring functions: 𝜒2 , ANOVA F-value, and the mutual information score. The F-value measures the linear dependency between the feature variable and the target. This means the score might underestimate the relation between a feature and the target if the relationship is nonlinear. The mutual information score is nonparametric and so can capture nonlinear relationships.
With SelectKBest, we define the number of features to keep, based on the score from the scoring function. Using .fit_transform(features, target) we get back an array with only the selected features.

```python
from sklearn.feature_selection import SelectKBest, f_classif
feature_cols = clicks.columns.drop(['click_time', 'attributed_time', 'is_attributed'])
train, valid, test = get_data_splits(clicks)

# Create the selector, keeping 40 features
selector = SelectKBest(f_classif, k=40)

# Use the selector to retrieve the best features
X_new = selector.fit_transform(train[feature_cols], train['is_attributed'])

# Get back the kept features as a DataFrame with dropped columns as all 0s
selected_features = pd.DataFrame(selector.inverse_transform(X_new),
                                index=train.index,
                                columns=feature_cols)

# Find the columns that were dropped
dropped_columns = selected_features.columns[selected_features.var() == 0]
```
