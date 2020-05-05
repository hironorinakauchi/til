# Convert timestamps

```python
ks = ks.assign(hour=ks.launched.dt.hour,
               day=ks.launched.dt.day,
               month=ks.launched.dt.month,
               year=ks.launched.dt.year)
```
[source](https://www.kaggle.com/matleonard/baseline-model)
