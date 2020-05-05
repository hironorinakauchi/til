# Calculate the number of previous app downloads
It's likely that if a visitor downloaded an app previously, it'll affect the likelihood they'll download one again. Implement a function previous_attributions that returns a Series with the number of times an app has been download ('is_attributed' == 1) before the current event.

```python
def previous_attributions(series):
    """ Returns a series with the """
    sums = series.expanding(min_periods=2).sum()-series
    return sums
```
