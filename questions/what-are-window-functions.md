# window functions in pandas

Window functions allow us to perform an operation with a given row’s data and data from another row that is a specified number of rows away — this “number of rows away value” is called the window.
<img src="https://miro.medium.com/max/1400/1*WAnIuMQZB40HfqOt5dzxVw.jpeg">

Window functions allow us to perform computations among the values of a specified column. For example, **I might want to compare today’s stock price with yesterday’s — then I would want a window of “1” looking backwards.** A window function allows us to do that. If on the other hand, I want to compare today’s price with the price 1 year ago, then I would want a window of “356” (assuming weekends are in your dataset).

Window functions are especially useful for time series data where at each point in time in your data, you are only supposed to know what has happened as of that point (no crystal balls allowed). The good news is that windows functions exist in pandas and they are very easy to use.

[source](https://towardsdatascience.com/window-functions-in-pandas-eaece0421f7)
