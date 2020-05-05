# count the number of events in the past x hours

i.g. the number of events from the same IP in the last six hours. 
It's likely that someone who is visiting often will download the app.

Implement a function count_past_events that takes a Series of click times (timestamps) and returns another Series with the number of events in the last hour. Tip: The rolling method is useful for this.
Because this can take a while to calculate on the full data, we'll load pre-calculated versions in the cell below to test model performance.

```python
def count_past_events(series, time_window='6h'):
    #flip the series and index
    series = pd.Series(series.index, index=series)
    past_events = series.rolling(time_window).count()-1
    return past_events
```
