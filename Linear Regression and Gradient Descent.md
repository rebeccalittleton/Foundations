Linear regression is the minimisation of the function defined by:
\[J(\beta) = 1/n * \sum_{i=1}^{n} (y_i - \hat{y}_i)^2\]
where \(y_i\) is the observed values and \(\hat{y}_i\) is our predicted value, this minimises the squared error of our prediction, thus the smaller the value of this function, 
the more accurate our model is.
The loss is then defined by:
\(y-\hat{y}\)

### Why do we use squared?
This penalises larger errors more
Smooth and differentiable which is ideal for an optimisation problem
