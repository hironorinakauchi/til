# how do you pick the best value of K
With this method we can choose the best K features, but we still have to choose K ourselves. How would you find the "best" value of K? That is, you want it to be small so you're keeping the best features, but not so small that it's degrading the model's performance.

To find the best value of K, you can fit multiple models with increasing values of K, then choose the smallest K with validation score above some threshold or some other criteria. A good way to do this is loop over values of K and record the validation scores for each iteration.
