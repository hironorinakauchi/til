# Count encode
Not included in the scikit-learn library but for the time being...

Count encoding replaces each categorical value with the number of times it appears in the dataset. For example, if the value "GB" occured 10 times in the country feature, then each "GB" would be replaced with the number 10.

```python
import category_encoders as ce
cat_features = ['category', 'currency', 'country']
count_enc = ce.CountEncoder()
count_encoded = count_enc.fit_transform(ks[cat_features])

data = baseline_data.join(count_encoded.add_suffix("_count"))

# Training a model on the baseline data
train, valid, test = get_data_splits(data)
bst = train_model(train, valid)
```


