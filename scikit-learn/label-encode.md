# Label Encode
For each of the categorical features ['ip', 'app', 'device', 'os', 'channel'], use scikit-learn's LabelEncoder to create new features in the clicks DataFrame. 

```python
from sklearn import preprocessing
#from sklearn.preprocessing import LabelEncoder

cat_features = ['ip', 'app', 'device', 'os', 'channel']

label_encoder = LabelEncoder()
# Create new columns in clicks using preprocessing.LabelEncoder()
for feature in cat_features:
    encoded = label_encoder.fit_transform(clicks[feature])
    clicks[feature + '_labels'] = encoded
```
