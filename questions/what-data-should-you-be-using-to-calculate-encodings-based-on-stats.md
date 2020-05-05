# what data should you be using to calculate the encodings based on stats
These encodings are all based on statistics calculated from the dataset like counts and means. Considering this, what data should you be using to calculate the encodings?
- Count Encoding
- Target Encoding
- Leave-one-out Encoding
- CatBoost Encoding
- Feature embedding with SVD

You should calculate the encodings **from the training set only**. If you include data from the validation and test sets into the encodings, you'll overestimate the model's performance. You should in general be vigilant to avoid leakage, that is, including any information from the validation and test sets into the model.
