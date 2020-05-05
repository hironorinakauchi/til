# Prepare target column

Once you have picked your target column, you then need to cook which typically involves a few steps of conversion, dropping and so on.

# figure out how many states are there
```python
pd.unique(ks.state)

'''
array(['failed', 'canceled', 'successful', 'live', 'undefined',
       'suspended'], dtype=object)
'''

# find out how many records of each
ks.groupby('state')['ID'].count()
'''
state
canceled       38779
failed        197719
live            2799
successful    133956
suspended       1846
undefined       3562
Name: ID, dtype: int64
'''
```

Data cleaning isn't the current focus, so we'll simplify this example by:
- Dropping projects that are "live"
- Counting "successful" states as outcome = 1
- Combining every other state as outcome = 0

```python
# Drop live projects
ks = ks.query('state != "live"')

# Add outcome column, "successful" == 1, others are 0
ks = ks.assign(outcome=(ks['state'] == 'successful').astype(int))
```
