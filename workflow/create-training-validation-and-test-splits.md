# Create training, validation, and test splits
need to create data sets for training, validation, and testing. We'll use a fairly simple approach and split the data using slices. We'll use 10% of the data as a validation set, 10% for testing, and the other 80% for training.

```python
valid_fraction = 0.1
valid_size = int(len(data) * valid_fraction)

train = data[:-2 * valid_size]
valid = data[-2 * valid_size:-valid_size]
test = data[-valid_size:]
```

In general you want to be careful that each data set has the same proportion of target classes. I'll print out the fraction of successful outcomes for each of our datasets.

```python
for each in [train, valid, test]:
    print(f"Outcome fraction = {each.outcome.mean():.4f}")

'''
Outcome fraction = 0.3570
Outcome fraction = 0.3539
Outcome fraction = 0.3542
'''
```

This looks good, each set is around 35% true outcomes likely because the data was well randomized beforehand. A good way to do this automatically is with `sklearn.model_selection.StratifiedShuffleSplit` but I don't need to use it here.



    
